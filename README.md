# EX-NO-11-ELLIPTIC-CURVE-CRYPTOGRAPHY-ECC

## Aim:
To Implement ELLIPTIC CURVE CRYPTOGRAPHY(ECC)


## ALGORITHM:

1. Elliptic Curve Cryptography (ECC) is a public-key cryptography technique based on the algebraic structure of elliptic curves over finite fields.

2. Initialization:
   - Select an elliptic curve equation \( y^2 = x^3 + ax + b \) with parameters \( a \) and \( b \), along with a large prime \( p \) (defining the finite field).
   - Choose a base point \( G \) on the curve, which will be used for generating public keys.

3. Key Generation:
   - Each party selects a private key \( d \) (a random integer).
   - Calculate the public key as \( Q = d \times G \) (using elliptic curve point multiplication).

4. Encryption and Decryption:
   - Encryption: The sender uses the recipient’s public key and the base point \( G \) to encode the message.
   - Decryption: The recipient uses their private key to decode the message and retrieve the original plaintext.

5. Security: ECC’s security relies on the Elliptic Curve Discrete Logarithm Problem (ECDLP), making it highly secure with shorter key lengths compared to traditional methods like RSA.

## Program:
```
p = 23
a = 1
b = 1
G = (9, 7)

def inv(x): return pow(x, p-2, p)

def add(P, Q):
    if P == Q:
        m = (3*P[0]*P[0] + a) * inv(2*P[1]) % p
    else:
        m = (Q[1]-P[1]) * inv(Q[0]-P[0]) % p

    x = (m*m - P[0] - Q[0]) % p
    y = (m*(P[0]-x) - P[1]) % p
    return (x, y)

def mul(k, P):
    R = P
    for _ in range(k-1):
        R = add(R, P)
    return R
a_priv = 6
b_priv = 11
A = mul(a_priv, G)
B = mul(b_priv, G)
keyA = mul(a_priv, B)
keyB = mul(b_priv, A)
print("Alice Public:", A)
print("Bob Public:", B)
print("Shared Key:", keyA)
```
## Output:
<img width="415" height="84" alt="image" src="https://github.com/user-attachments/assets/ad91075d-8460-4d10-b3bd-c2a06ab30c7e" />

## Result:
The program is executed successfully.

