import math
import time


""" função auxiliar para calcular o número ímpar mais próximo anterior"""
def nearestOddUnder(number):
    if (number % 2) == 0:
        number = number -1
    else:
        number = number -2
    return number

""" funções auxiliares para fazer o modulo inverso """
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, y, x = egcd(b % a, a)
        return (g, x - (b // a) * y, y)

def modinv(a, m):
    g, x, y = egcd(a, m)
    if g != 1:
        raise Exception('modular inverse does not exist')
    else:
        return x % m

def bruteRSA(n,e):
    start_time = time.time()
    c = math.floor((math.sqrt(n)))
    c = nearestOddUnder(c)
    """ descobrindo por força bruta o número o p """
    for i in range(c, 1 , -2):
        if(n%i == 0):
            p = i
            break
    """ descoberto o p, é fácil descobrir o q """
    q = n /p 
    q = math.floor(q)
    """ eu sei que o cálculo funcionou porque p*q deu zero """
    if (n -p*q) != 0:
        raise Exception('não deu certo')
    """aqui começa o cálculo do d, em que d*e %phin tem que dar 1 pra termos a chave correta """
    phin = (p-1) * (q-1)
    d = modinv(e,phin)
    if (d*e %phin != 1):
         raise Exception('não deu certo')

    total_time = time.time() - start_time
    return (d,total_time)


""" essas são as chaves, uma tupla (n,e) """
arr = [(1325147,79), (13339787,351047),(87411743,11),(153988391,365), (642281891,80105) ,(3662937263, 80273),(2461987247,78703) ,(10988963221,118297),(9979645019,9764819), (36207914857,89  )]
tempototal = 0
for val in arr:
    chave, tempo = bruteRSA(*val)
    n1,e1 = val
    print('esse é o par',n1,e1)
    print('a chave é', chave)
    print('esse demorou', tempo)
    tempototal += tempo


print('o tempo total foi de',tempototal)
