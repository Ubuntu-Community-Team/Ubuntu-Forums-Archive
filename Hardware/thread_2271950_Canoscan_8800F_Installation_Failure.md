---
title: "Canoscan 8800F Installation Failure"
date: 2015-04-02
forum: Hardware
---

### Post by drumone on 2015-04-02
I've searched the forums and done every blasted step suggested to get this stupid scanner to work to no avail. I have a Canon Canoscan 8800F and I'm running Ubuntu 14.04 LTS. My system itself can handle the scanner just fine. I know this because it works on the Windows side of things. Can anyone help me out with this? I'm not a programmer and I don't know squat about writing code (I use Linux because I hate the bastards at Microsoft and Apple is too expensive for me as a teacher). I love Ubuntu, but this is making me reconsider my dual boot situation. Any suggestions for the average idiot (me) would be greatly appreciated. Thanks.

---

### Post by aikishugyo on 2015-04-03
Hello Neil,
Since I wrote the support for the 8800F in the sane backends code, here are some suggestions:

[LIST=1]
[*] make sure your sane-backends is new enough to support the Canoscan 8800F. If you are using 1.0.24 or 1.0.25 no problem I think. You can check the SANE website to check from which Canon pixma backend support was added, and "man sane-pixma" will give you the info about your currently installed pixma backend.
[*] if you need to get a new sane-backends, you will can get Ubuntu packages from the current (excellent) developer's repository---search the forums or the sane-devel mailing list.
[*] You might want to read the linux README included with the package, since it gives helpful advice for permission settings and other stuff that you might need in order to be able to scan as a non-root user.
[/LIST]
Regards,
Gernot Hassenpflug

---

