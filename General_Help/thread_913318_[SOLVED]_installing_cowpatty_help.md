---
title: "[SOLVED] installing cowpatty help"
date: 2008-09-07
forum: General Help
---

### Post by chex_m8 on 2008-09-07
i'm trying to install cowpatty. when i did the make command it gave an error. see pic. can someone tell me whats wrong, thx.

---

### Post by chex_m8 on 2008-09-07
I solved it,

---

### Post by re98001 on 2008-09-10
Can you please explain how you fixed your problem? I got the same problem. Thanks.

---

### Post by n4p1 on 2008-09-10
apt-get install libssl-dev
apt-get install libpcap0.8-dev
then try make.

---

### Post by pixelot on 2008-10-26
Nice. It worked. :)

---

### Post by sunilsattiraju on 2008-11-07
hi,
I got the below warning while "make" command 

cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o sha1.o sha1.c
In function ‘memcpy’,
    inlined from ‘hmac_sha1_vector’ at sha1.c:111:
/usr/include/bits/string3.h:52: warning: call to __builtin___memcpy_chk will always overflow destination buffer
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o utils.o utils.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o cowpatty.o cowpatty.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o genpmk.o genpmk.c
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result
genpmk.c:278: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:279: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:280: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb genpmk.c -o genpmk utils.o sha1.o -lpcap -lcrypto
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result
genpmk.c:278: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:279: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:280: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result

am i missing something ? pls help

Thanks

---

### Post by Hex on 2008-12-04
I have the same problem, anyone have any ideas?

---

### Post by B34ST1Y on 2008-12-23
bump* - I'm having that error too. Anyone with knowledge on the subject, please help!

---

### Post by B34ST1Y on 2008-12-23
double post, sorry.

---

### Post by albinootje on 2008-12-23
Dear people, how nice and delightful of you to be auditing your own wifi-networks against attacks from the outside ;-)
> **sunilsattiraju said:**
> 
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb genpmk.c -o genpmk utils.o sha1.o -lpcap -lcrypto
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result

Just out of curiosity i've just successfully compiled cowpatty 4.3 on Ubuntu 8.10.
It also needed : 
```

sudo apt-get install libdigest-hmac-perl

```

---

### Post by raybonz420 on 2009-02-28
I could use some help im sorry if i posted in the wrong one.
here is the error i get when i run make 

cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
md5.c:20:25: error: openssl/md5.h: No such file or directory
md5.c: In function &#8216;md5_mac&#8217;:
md5.c:28: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
md5.c:28: error: (Each undeclared identifier is reported only once
md5.c:28: error: for each function it appears in.)
md5.c:28: error: expected &#8216;;&#8217; before &#8216;context&#8217;
md5.c:29: warning: implicit declaration of function &#8216;MD5_Init&#8217;
md5.c:29: error: &#8216;context&#8217; undeclared (first use in this function)
md5.c:30: warning: implicit declaration of function &#8216;MD5_Update&#8217;
md5.c:33: warning: implicit declaration of function &#8216;MD5_Final&#8217;
md5.c: In function &#8216;hmac_md5_vector&#8217;:
md5.c:40: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
md5.c:40: error: expected &#8216;;&#8217; before &#8216;context&#8217;
md5.c:48: error: &#8216;context&#8217; undeclared (first use in this function)
make: *** [md5.o] Error 1

please help i am very new to linux/ubuntu

---

### Post by maquereautin on 2009-06-23
I have been reading and reading about how to compile and install cowpatty, but i haven't made much progress. I've downloaded cowpatty 4.2, but thats about as far as i have gotten. 

I ran the command below to get build-essential, it said done but now i'm confused again. How do i use build-essential to make cowpatty?
sudo aptitude install build-essential

---

### Post by Hex on 2009-08-24
> **albinootje said:**
> Dear people, how nice and delightful of you to be auditing your own wifi-networks against attacks from the outside ;-)


Just out of curiosity i've just successfully compiled cowpatty 4.3 on Ubuntu 8.10.
It also needed : 
```

sudo apt-get install libdigest-hmac-perl

```

This didn't quite help, but thank you for the effort and comments.

---

### Post by Skylancer on 2009-09-01
I had successfully compiled Cowpatty 4.3 on Ubuntu 9.10 (Linux Mint 7).
I did the following:
```
sudo -s
apt-get install libssl-dev
apt-get install libpcap0.8-dev
apt-get install libdigest-hmac-perl
```
make (from inside cowpatty directory unpacked in the home folder)
```
aptitude install build-essential
cowpatty
```

I confirmed that cowpatty was working by accessing the help and running a test sample.
Hope this helps others.

---

### Post by Ana7h3ma on 2009-09-02
good job Skylancer :D:
only one thing left before insert cowpatty in console:

```
sudo cp cowpatty /usr/bin
```

now you are ready to use the program only writing

```
cowpatty
```

bye

---

### Post by wadiw on 2010-06-02
no work, making all theses steps:
<_**cowpatty: command not found**_>

pls help

---

### Post by teh_pwnzr on 2010-11-04
> **n4p1 said:**
> apt-get install libssl-dev
apt-get install libpcap0.8-dev
then try make.
 
This worked for me on Ubuntu 9.10 with CowPatty 4.6
 
Also, to execute, do "./cowpatty" after making it.

---

### Post by tekal on 2011-03-15
> **n4p1 said:**
> apt-get install libssl-dev
apt-get install libpcap0.8-dev
then try make.

Worked for me! 

A hint:
Worked for me together with "sudo" and do the "make" inside the folder you unpacked cowpatty.

---

