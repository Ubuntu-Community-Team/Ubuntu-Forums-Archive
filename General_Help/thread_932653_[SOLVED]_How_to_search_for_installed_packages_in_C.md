---
title: "[SOLVED] How to search for installed packages in CLI"
date: 2008-09-28
forum: General Help
---

### Post by philidox on 2008-09-28
I would like to know how to search for previously installed packages in Ubuntu's command line interface.

I know how to search for packages(sudo apt-cache search filename)
I know how to installed packages (sudo apt-get install filename)

I just don't know search for packages that are already on Ubuntu machine.

---

### Post by drs305 on 2008-09-28
```
sudo dpkg --get-selections > ~/Desktop/installed.packages
```

---

### Post by howefield on 2008-09-28
yeah, what he said... :)

---

### Post by kerry_s on 2008-09-28
in terminal:

```
dpkg --get-selections | more
```

---

### Post by philidox on 2008-09-29
> **drs305 said:**
> ```
sudo dpkg --get-selections > ~/Desktop/installed.packages
```

So if I think I installed a deb packaged named  "acidrip" and I wanted to see it through the cli I would type **sudo dpkg --get-selections acidrip**.

---

### Post by drs305 on 2008-09-29
> **philidox said:**
> So if I think I installed a deb packaged named  "acidrip" and I wanted to see it through the cli I would type **sudo dpkg --get-selections acidrip**.

No, running the following command would simply create a file called "installed.packages" on your desktop. You could open it to see if the package was listed and it's status:
```
sudo dpkg --get-selections > ~/Desktop/installed.packages
```
The original reply was to return a list of *all* the packages installed on your system.

To see if a single package was installed, one way would be to enter:
```
aptitude show acidrip
```
It will show the status (installed/not installed) on the third line of the return  -State: -
You could reduce the return specifically to the 'State' by running:
```
aptitude show acidrip | grep 'State'
```

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

