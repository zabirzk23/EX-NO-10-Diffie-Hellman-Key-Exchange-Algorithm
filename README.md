# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```
#include <stdio.h>
long long mod_exp(long long base, long long exp, long long mod) {
 long long res = 1;
 while (exp) {
 if (exp & 1) res = (res * base) % mod;
 base = (base * base) % mod;
 exp >>= 1;
 }
 return res;
}
int main() {
 long long P, G, a, b, x, y, ka, kb;
 printf("**** Diffie-Hellman Key Exchange ****\n");
 printf("Enter prime P and primitive root G: "); scanf("%lld%lld", &P, &G);
 printf("Enter Alice's private key a: "); scanf("%lld", &a);
 printf("Enter Bob's private key b: "); scanf("%lld", &b);
 x = mod_exp(G, a, P);
 y = mod_exp(G, b, P);
 ka = mod_exp(y, a, P);
 kb = mod_exp(x, b, P);
 printf("Alice's public key: %lld\nBob's public key: %lld\n", x, y);
 printf("Shared key (Alice): %lld\nShared key (Bob): %lld\n", ka, kb);
 printf(ka == kb ? "\nKey exchange successful.\n" : "\nKey mismatch error.\n");
 return 0;
}
```

## Output:

<img width="618" height="445" alt="image" src="https://github.com/user-attachments/assets/1f4dc457-20ec-4398-8a76-ac821da04a2e" />


## Result:
  The program is executed successfully

