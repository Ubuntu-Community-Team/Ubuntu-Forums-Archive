---
title: "Can't get New Brother Laser printer/scanner to scan"
date: 2019-11-26
forum: Hardware
---

### Post by cybrsaylr on 2019-11-26
Got a new Brother laser printer HL-L 2390DW.
Installed it with Windows 10 and it works fine.


Installed this Brother printer on my desktop running Ubuntu 18.04.3 LTS and it runs and copies documents fine using Firefox, Chrome and Vivaldi. It will copy documents fine but I can't get it to scan. Tried using Simple Scan which reports it can't fine any scan device. 

Help?
What needs to be done to make the scan feature work?

---

### Post by brian_p on 2019-11-26
What does ```
dpkg -l libsane
``` give?

---

### Post by cybrsaylr on 2019-11-26
brian_p
It gives this:
> $ dpkg -l libsane
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  libsane        <none>       <none>       (no description available)


---

### Post by cybrsaylr on 2019-11-26
Don't understand what that terminal output means.

---

### Post by brian_p on 2019-11-27
A typo on my part. This is the corrected command: ```
dpkg -l libsane1
```

---

### Post by The Cog on 2019-11-27
I suspect that Brian is trying to find out wether libsane is installed, but I can't be sure. I don't know much (anything) about scanner drivers, excet that libsane is something to do with driving scanners. This command will reliably tell you whether libsane is installed, even with the minor name changes it has undergone. Posting the result of that might help people figure things out:
```
apt search libsane
```
It is better to use CODE tags than QUOTE tags when posting output like this. Much easier for others to read. You can change QUOTE to CODE in the quick reply, or if you click Go Advanced, you get a # button that directly inserts CODE tags.

---

### Post by SeijiSensei on 2019-11-27
Did you use the Driver Install Tool from the Brother website? That will reliably install the drivers your device needs. Enter your model number on this page to get the tool: [https://www.brother-usa.com/brother-support/driver-downloads](https://www.brother-usa.com/brother-support/driver-downloads)

---

### Post by cybrsaylr on 2019-11-27
brain_p

Got this output:

```
~$ dpkg -l libsane1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libsane1:amd64 1.0.27-1~exp amd64        API library for scanners
```

The Cog

Got this output: 

```
~$ apt search libsane
Sorting... Done
Full Text Search... Done
libghc-bindings-sane-dev/bionic 0.0.1-10build1 amd64
  FFI bindings to libsane

libghc-bindings-sane-doc/bionic,bionic 0.0.1-10build1 all
  FFI bindings to libsane

libghc-bindings-sane-prof/bionic 0.0.1-10build1 amd64
  FFI bindings to libsane

libreoffice/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
  office productivity suite (metapackage)

libsane-common/bionic-updates,bionic-updates,now 1.0.27-1~experimental3ubuntu2.2 all [installed]
  API library for scanners -- documentation and support files

libsane-dev/bionic-updates,now 1.0.27-1~experimental3ubuntu2.2 amd64 [installed]
  API development library for scanners [development files]

libsane-extras/bionic 1.0.22.5 amd64
  API library for scanners -- extra backends

libsane-extras-common/bionic,bionic 1.0.22.5 all
  API library for scanners -- documentation and support files

libsane-extras-dev/bionic 1.0.22.5 amd64
  API development library for scanners [development files]

libsane-hpaio/bionic,now 3.17.10+repack0-5 amd64 [installed]
  HP SANE backend for multi-function peripherals

libsane1/bionic-updates,now 1.0.27-1~experimental3ubuntu2.2 amd64 [installed]
  API library for scanners
```

SeijiSensei 

Went to  the Driver Install Tool from the Brother website and am trying to figure out just what to do.
It appears simple but not really sure how to use it!

---

### Post by brian_p on 2019-11-27
Thanks. Just ensure your version is the most up-to-date. There has been a bug in libsane1 which affected many users.

---

### Post by brian_p on 2019-11-27
Please post what you get for ```
ls -l /usr/lib/sane/libsane-brother*
``` and ```
ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-brother*
```

---

### Post by cybrsaylr on 2019-11-27
brian got this:

```
~$ ls -l /usr/lib/sane/libsane-brother*
ls: cannot access '/usr/lib/sane/libsane-brother*': No such file or directory

~$ ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-brother*
ls: cannot access '/usr/lib/x86_64-linux-gnu/sane/libsane-brother*': No such file or directory

```

---

### Post by cybrsaylr on 2019-11-27
Have contacted Brother and today they sent me a 'fix' that upon reading is more detailed, complex and complicated than the link shown in this thread by SeijiSensei in post 7!

---

### Post by brian_p on 2019-11-27
It very much looks like you do not have the Brother scanner driver installed. Give me 5/10 minutes and I will describe what I would do.

---

### Post by cybrsaylr on 2019-11-27
Thanks brian.

Tried doing what was shown in the link shown in this thread by SeijiSensei in post 7 but couldn't figure it out!

---

### Post by brian_p on 2019-11-27
[list]Go to [https://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=hll2390dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=hll2390dw_us&os=128)  and select the 64bit scanner driver.[/list]

[list]Agree to the EULA and download **brscan4-0.4.8-1.amd64.deb.**

[LIST]
Go to the directory holding **brscan4-0.4.8-1.amd64.deb.** and execute ```
apt install ./brscan4-0.4.8-1.amd64.deb
```
[/LIST]

Do the previous *ls -l...* commands now give a positive output? Can you now scan?

---

### Post by cybrsaylr on 2019-11-27
brian get this now for your 2 codes: 

```
~$ ls -l /usr/lib/sane/libsane-brother*
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/sane/libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/sane/libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/sane/libsane-brother4.so.1.0.7 -> /usr/lib64/sane/libsane-brother4.so.1.0.7

~$ ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-brother*
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root 41 Nov 27 13:40 /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7 -> /usr/lib64/sane/libsane-brother4.so.1.0.7

```

Printer works on printing but still won't scan.

---

### Post by brian_p on 2019-11-27
> Printer works on printing but still won't scan.

To get one thing out of the way: printing and scanning are completely different processes. There is no connection between them. It doesn't help to think that way.

We need the output of ```
ls -l /usr/lib64/sane
```

---

### Post by cybrsaylr on 2019-11-27
brian here's that output:

```
~$ ls -l /usr/lib64/sane
total 196
lrwxrwxrwx 1 root root     37 Apr 25  2019 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1
lrwxrwxrwx 1 root root     41 Apr 25  2019 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
-rwxr-xr-x 1 root root 198360 Apr 25  2019 libsane-brother4.so.1.0.7

```

Yes I realize printing and scanning are completely different processes. At least the copy feature works fine which I believe functions much like scanning....i hope.

---

### Post by brian_p on 2019-11-27
> **cybrsaylr said:**
> brian here's that output:

```
~$ ls -l */usr/lib64/sane*
total 196
lrwxrwxrwx 1 root root     37 Apr 25  2019 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1
lrwxrwxrwx 1 root root     41 Apr 25  2019 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
-rwxr-xr-x 1 root root 198360 Apr 25  2019 libsane-brother4.so.1.0.7

```


Brother seems completely unaware that Debian libsane1 does not look in */usr/lib64/sane* for SANE drivers, yet it puts the there. So much for supporting Mint. Something drastic (and probably my last try):

```
cp /usr/lib64/sane/libsane-brother4* /usr/lib/x86_64-linux-gnu/sane/
```

I hope you have updated your installation, as advised.

---

### Post by cybrsaylr on 2019-11-27
My Ubuntu 18.04.3 LTS is always kept up to date.

Got this output for your (last try) code:

```
~$ cp /usr/lib64/sane/libsane-brother4* /usr/lib/x86_64-linux-gnu/sane/
cp: '/usr/lib64/sane/libsane-brother4.so' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so' are the same file
cp: '/usr/lib64/sane/libsane-brother4.so.1' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1' are the same file
cp: '/usr/lib64/sane/libsane-brother4.so.1.0.7' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7' are the same file

```

---

### Post by brian_p on 2019-11-27
Scanning?

---

### Post by brian_p on 2019-11-27
> **cybrsaylr said:**
> My Ubuntu 18.04.3 LTS is always kept up to date.

Got this output for your (last try) code:

```
~$ cp /usr/lib64/sane/libsane-brother4* /usr/lib/x86_64-linux-gnu/sane/
cp: '/usr/lib64/sane/libsane-brother4.so' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so' are the same file
cp: '/usr/lib64/sane/libsane-brother4.so.1' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1' are the same file
cp: '/usr/lib64/sane/libsane-brother4.so.1.0.7' and '/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7' are the same file

```

Some thinking in the pipline. It may take a while.

---

### Post by cybrsaylr on 2019-11-27
Success! 

Opened up Simple Scan and it recognized the Brother printer/scanner, straightaway saying it's ready to scan.
Put a document on the scanner glass, hit scan and Simple Scan did the rest. Scanned the doc to PC monitor, then was able to print the scanned doc out with Brother!

Those drivers must have done the trick, after opening up and using Simple Scan. Should have tried this earlier.

Thanks for all the help brian!!!



BTW also have XSane Image scanning program installed.
Just opened up XSane and it seems to be working also and XSane recognized the Brother printer/scanner also.
XSane seems more elaborate than Simple Scan and appears also ready to run.

---

### Post by Paulgirardin on 2019-12-02
> **brian_p said:**
> Brother seems completely unaware that Debian libsane1 does not look in */usr/lib64/sane* for SANE drivers, yet it puts the there. So much for supporting Mint. Something drastic (and probably my last try):

```
cp /usr/lib64/sane/libsane-brother4* /usr/lib/x86_64-linux-gnu/sane/
```

I hope you have updated your installation, as advised.

Yes.It has been like this for years.
At every OS upgrade I have to create symlinks for the driver files in various directories to get my MFC 3220 scanning.

For the OP: XSANE is superior to Simple Scan for anything more than a simple scan

---

### Post by cmcanulty on 2019-12-03
this is not a fix for the specific issue but may help people with scanning problems. It has fixed mine on several computers. Make sure you are a member of scanner group in: users and groups-scanner group

---

### Post by cybrsaylr on 2019-12-05
> **Paulgirardin said:**
> For the OP: XSANE is superior to Simple Scan for anything more than a simple scan
Thanks.

Noticed that after opening XSANE up. It kinda reminded me of Gimp.

---

