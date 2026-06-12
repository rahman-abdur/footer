#include <iostream>
using namespace std;

int main() {
    int n, capacity;

    cout << "Enter number of items: ";
    cin >> n;

    float weight[100], profit[100], ratio[100];

    for(int i = 0; i < n; i++) {
        cout << "Weight and Profit of item " << i + 1 << ": ";
        cin >> weight[i] >> profit[i];

        ratio[i] = profit[i] / weight[i];
    }

    cout << "Enter knapsack capacity: ";
    cin >> capacity;

    // Sort by profit/weight ratio (descending)
    for(int i = 0; i < n - 1; i++) {
        for(int j = i + 1; j < n; j++) {
            if(ratio[i] < ratio[j]) {

                float temp;

                temp = ratio[i];
                ratio[i] = ratio[j];
                ratio[j] = temp;

                temp = weight[i];
                weight[i] = weight[j];
                weight[j] = temp;

                temp = profit[i];
                profit[i] = profit[j];
                profit[j] = temp;
            }
        }
    }

    float totalProfit = 0;

    for(int i = 0; i < n; i++) {

        if(capacity >= weight[i]) {
            totalProfit += profit[i];
            capacity -= weight[i];
        }
        else {
            totalProfit += ratio[i] * capacity;
            break;
        }
    }

    cout << "Maximum Profit = " << totalProfit << endl;

    return 0;
}
------------------------------------------------------------
#Selection



#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of activities: ";
    cin >> n;

    int start[100], finish[100];

    for(int i = 0; i < n; i++) {
        cout << "Start and Finish time of activity " << i + 1 << ": ";
        cin >> start[i] >> finish[i];
    }

    // Sort activities by finish time
    for(int i = 0; i < n - 1; i++) {
        for(int j = i + 1; j < n; j++) {
            if(finish[i] > finish[j]) {

                int temp;

                temp = finish[i];
                finish[i] = finish[j];
                finish[j] = temp;

                temp = start[i];
                start[i] = start[j];
                start[j] = temp;
            }
        }
    }

    cout << "\nSelected Activities:\n";

    int count = 1;
    cout << "(" << start[0] << ", " << finish[0] << ")" << endl;

    int lastFinish = finish[0];

    for(int i = 1; i < n; i++) {
        if(start[i] >= lastFinish) {
            cout << "(" << start[i] << ", " << finish[i] << ")" << endl;
            count++;
            lastFinish = finish[i];
        }
    }

    cout << "\nMaximum activities = " << count << endl;

    return 0;
}
----------------------------------
Coin##
#include <iostream>
using namespace std;

int main() {
    int n, amount;

    cout << "Enter number of coin types: ";
    cin >> n;

    int coin[100];

    cout << "Enter coin values: ";
    for(int i = 0; i < n; i++) {
        cin >> coin[i];
    }

    cout << "Enter amount: ";
    cin >> amount;

    int count = 0;

    cout << "Coins used: ";

    for(int i = 0; i < n; i++) {
        while(amount >= coin[i]) {
            cout << coin[i] << " ";
            amount -= coin[i];
            count++;
        }
    }

    cout << "\nTotal coins = " << count << endl;

    return 0;
}

-----------------------

#include <iostream>
using namespace std;

int factorial(int n) {
    if(n == 0 || n == 1) {
        return 1;   // base case
    }
    return n * factorial(n - 1);  // recursive call
}

int main() {
    int n;

    cout << "Enter a number: ";
    cin >> n;

    cout << "Factorial = " << factorial(n) << endl;

    return 0;
}

