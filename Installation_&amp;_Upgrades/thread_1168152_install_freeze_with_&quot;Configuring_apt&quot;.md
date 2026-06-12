---
title: "install freeze with &quot;Configuring apt&quot;"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by jfmdad on 2009-05-23
Inst5alled 9.04 from CD on PC running win7 - great success!, now trying same procedure on other PC. Installing to new formatted ext3, the install freezes at "Configuring apt" and subtext "scanning the mirror". progress bar says 82% finished.
Any one out there have a solution?

---

### Post by taurus on 2009-05-23
1.  Does the network connection on that machine work at all?

2.  How long have you waited for the "scanning for mirror" message?

---

### Post by jfmdad on 2009-05-23
Network connection ok, when running win7 (erased now).
tried install in safe graphics mode, now stop at 82% but reporting Scanning the security updates repository....

What the hell is happening. Can it be something connected to my graphics card?

):P

---

### Post by taurus on 2009-05-23
Scanning for security updates has nothing to do with your graphic card.  Do you need to configure proxy before you can get out on the net?  If you wait long enough, it would time out and continues with the rest of the installation.

---

### Post by jfmdad on 2009-05-23
thx. I will try the waiting procedure.
I know the message is not related to my graphic card, but why a new message at 82% installed when only the safe graphic option has changed?
I just try again and hope.

---

### Post by jfmdad on 2009-05-24
Problem is that install do not detect my wireless adaptor.
The adaptor is a TRENDnet TEW-423PI.
ANYONE OUT THERE WITH A SOLUTION?

---

### Post by jfmdad on 2009-05-24
I have seen plenty of advices about using TEW-423PI, but my problem is that I cant use them because I can install withoput a netconnection!

---

### Post by yusufu on 2009-06-05
I had the same problem (installation freezing at 82% on *configuring apt*) when installing gos which is based on ubuntu. Since my connection to the net was through proxy  the installation was trying to access the internet but  it could not get through because it didnt have the username and  password supplied.  What I did was to simply  remove the network cable ( or disable any connection  to the internet  e.g wireless). The installation will gennerate a warning but you can simply click the dialogue and the installation will continue.:D

---

