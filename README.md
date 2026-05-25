# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Vishvabala
RegisterNumber: 212225040496
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np

def qr_decomposition(A):
    A = np.array(A, dtype=float)
    m, n = A.shape

    Q = np.zeros((m, n))
    R = np.zeros((n, n))

    for k in range(n):
        v = A[:, k]

        for j in range(k):
            R[j, k] = np.dot(Q[:, j], A[:, k])
            v = v - R[j, k] * Q[:, j]

        R[k, k] = np.linalg.norm(v)
        Q[:, k] = v / R[k, k]

    return Q, R


# Input matrix
A =eval(input())

Q, R = qr_decomposition(A)

print("The Q Matrix is\n", Q)
print("The R Matrix is\n", R)

```

## Output
```
<img width="1256" height="806" alt="image" src="https://github.com/user-attachments/assets/2e3a43ea-ba57-4f8d-ba20-e9caeeaf2448" />

<img width="1247" height="605" alt="image" src="https://github.com/user-attachments/assets/e082ad38-cee3-4909-b47f-819cb478bd1c" />

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
