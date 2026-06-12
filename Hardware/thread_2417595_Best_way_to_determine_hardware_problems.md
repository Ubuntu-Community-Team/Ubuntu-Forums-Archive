---
title: "Best way to determine hardware problems?"
date: 2019-04-24
forum: Hardware
---

### Post by wally1960 on 2019-04-24
Hello, My desktop keeps freezing up. This dosen't matter what distro I'm using. I'm currently using Lubuntu16.04. Which was rock solid up to last week. I'm sure something is wrong with the motherboard. I'm using this problem as a learning experience. I used memtest86+, which showed no problems with ram. I did a short hard drive test, nothing. I'd like to try  an all in one check software, but i'm concerned this would put too much stress on a possible messed up board. It will be a few weeks before I can buy a new one. What are your suggestions?
Thank's in advance for any help.

---

### Post by mörgæs on 2019-04-25
If your computer has more than one memory stick then remove them one at a time to see if anything changes. A good and easy test also when Memtest does not show any errors.

After that a fresh install of Lubuntu 18.04 or 19.04.

---

### Post by Rubi1200 on 2019-04-25
Open the terminal CTRL+ALT+T and install the following package:

```
sudo apt-get install inxi
```

Once installed run this:

```
inxi -b
```

Post the results here please in code tags (Go Advanced look for # and paste text between).

Sometimes best to just do a clean install after backing up but let's look at the hardware specs. (reason for code above).

Thanks.

---

### Post by TheFu on 2019-04-25
I agree with both posts above by Rubi1200 and mörgæs.
Have you looked at the log files?  Usually hardware errors will show up in some form of log.

```
sudo egrep -i 'err|warn' /var/log/*g
```
will find all the errors and warnings. Might want to redirect that output to a file in /tmp/ for reading or use a PAGER like less or more.  Hopefully, there aren't many, but if something bad is happening, it could be lots-o-output.

---

### Post by wally1960 on 2019-04-25
Thanks for the help gentlemen. No need to continue this board is crapped out.

---

### Post by jiahuaguang on 2019-04-26
[FONT=Roboto]**How to Diagnose a Computer Problem**[/FONT]
[FONT=Roboto]
[LIST]
[*]Check the POST. ...
[*]Notice the load time of the OS (operating system). ...
[*]Notice any graphics problems once the OS has loaded. ...
[*]Perform an auditory test. ...
[*]Check any newly installed hardware. ...
[*]Check any newly installed software. ...
[*]Check RAM and CPU consumption.
[/LIST]
[/FONT]

---

