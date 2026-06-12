---
title: "Has anyone ever got a Canon Pixma MP160 printer working?"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Eoghanalbar on 2007-06-10
And how?

---

### Post by Pragmatist on 2007-06-10
Try this:

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

---

### Post by DBStevens on 2007-06-10
Does the printer support post script if so it should be able to be setup under CUPS. 

I just don't see that printer listed as one of the 3128 on:

[http://www.easysw.com/cups/printers.php?START=0&MAKE=&MODEL=](http://www.easysw.com/cups/printers.php?START=0&MAKE=&MODEL=)

I also don't have the manual for that particular printer.   If you do and there is a .ppd on the setup CD you should have better than a fair chance of it working without too much hastle.

<edit> Ah I see from another poster it does have a .ppd </edit>

---

### Post by Eoghanalbar on 2007-06-10
Pragmatic, I already saw that page yesterday, and got stuck somewhere tween step 2 and 3. Today I managed to get everything except for step 6 done.

```
root@o1:/home/o1# sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usblp0 -E
lpadmin: No such file or directory

```

What do I do about that?

---

### Post by Pragmatist on 2007-06-10
Please post the results of these:

```
ls -l /home/ol/canonmp160.ppd
```

```
ls -l /dev/usblp0
```

---

### Post by Eoghanalbar on 2007-06-10
The first one returns "no such file or directory". I screwed around for a while and finally found that this worked:

```
o1@o1:~$ ls -l /home/o1/usr/share/cups/model
total 12
-rw-r--r-- 1 o1 admin 11022 2007-06-10 16:00 canonmp160.ppd

```

Why does it find it when I searched specifically for "canonmp160.ppd", but when I tried to find ANY .ppd files by searching for "*.ppd" (I also tried "?.ppd" in case I'd gotten the single character and any character thingies mixed up) it didn't work?

Anyway, it also said that it was already installed.

Is it okay that "I" am the owner, or should it belong to root? I dunno, I'm just making totally random useless guesses here, aren't I?

Maybe here's a better guess: should I move the file or should I change it to the following?

```
sudo lpadmin -p MP160 -P /home/o1/usr/share/cups/model/canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

```

When I put that in the terminal it just accepts it with no sign that anything happened at all.



The other list you asked for returns this:

```
o1@o1:~$ ls -l /dev/usblp0 
crw-rw---- 1 root lp 180, 0 2007-06-10 18:55 /dev/usblp0

```

---

### Post by Pragmatist on 2007-06-10
> **Eoghanalbar said:**
> ...Why does it find it when I searched specifically for "canonmp160.ppd", but when I tried to find ANY .ppd files by searching for "*.ppd" (I also tried "?.ppd" in case I'd gotten the single character and any character thingies mixed up) it didn't work?

What is the exact command you typed?  Were you using "locate" or "find" or some other search program?

> **Eoghanalbar said:**
>  Anyway, it also said that it was already installed.
What said that it was already installed (i.e. what is "it"?)?

> **Eoghanalbar said:**
> 
```
sudo lpadmin -p MP160 -P /home/o1/usr/share/cups/model/canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

```When I put that in the terminal it just accepts it with no sign that anything happened at all.


Does the printer work after you ran that command?

---

### Post by Eoghanalbar on 2007-06-10
I searched using the GUI file browser.

Sorry, the "it" that said the driver was already installed was the "install drivers" under "printer properties" under menus [System > Administration > Printing]

No, you'll hear about it when it finally works, dude :P

I now have one printer according to  [System > Administration > Printing]. It's called "MP160", and it has one job pending, a test page. It's location was nothing, so I tried setting it to "/dev/usblp0". No luck

The actually physical machine is just sitting there with the "ON/OFF" switch glowing green and not doing anything.

---

### Post by Pragmatist on 2007-06-10
Just out of curiosity, what happens if you press the printer button while a job is pending?  The reason I ask, is because I had a situation, when I used this particular printer driver, where I had to actually press the printer button while the job was pending.

---

### Post by Pragmatist on 2007-06-10
Also, try printing a simple text file using the "lpr" command.  Either create a test document that is about a page in length (i.e. more than a couple of sentences), or just use some text file that is about that size.  Then type this:

```
lpr filename
```

---

### Post by Eoghanalbar on 2007-06-11
Now jobs that I add just randomly disappear after something like ten seconds.

Pressing the start button on the printer spits out a page with nothing on it, whether there was a job or not.

```
lpr: Error - no default destination available.
```

And yet MP160 does claim to be the default in the "Printers" window.

---

### Post by Pragmatist on 2007-06-11
So, just to verify, you exactly followed, in order, all 7 steps in the above link?

---

### Post by Eoghanalbar on 2007-06-11
Except for the modification to the path of the canonmp160.ppd file, yes.

---

### Post by Pragmatist on 2007-06-11
What happens if you run this command:
```
cngpij -P MP160 filename
```

---

### Post by Eoghanalbar on 2007-06-11
I reinstalled ubuntu last night, figuring maybe doing everything fresh with a somewhat better idea how it works would help.

I tried [the instructions at openprinting.org]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160") again, but this time I can't find a "canonmp160.ppd" file anywhere on the computer.

I'm thinking at this point the best use of my time is to retreat and set up a dual boot.

Oh, and Pragmatist, thanks a lot for everything. You're an awesome guy, really. 

Everyone else who helped me with stuff too, even if they absentmindedly crammed a post full of ten new bits of unexplained jargon all at once :p

---

### Post by Pragmatist on 2007-06-11
A dual boot is an excellent idea.  That is the way most people start with Linux.

My guess is that eventually your printer will be supported without your having to do anything.  The printer you have is very new, so it sometimes take a little time.  However, people have already gotten your printer to work, on Ubuntu no less, so at least we know it is possible.  In this case, however, it does require a certain level of skill above that of a typical newcomer.

---

### Post by imotlaw on 2007-06-21
I'd like to pick up where Eoghanalbar left off. I'm using Xubuntu Feisty 7.04, have completed (successfully, as far as I can tell) all of the steps in the openprint.org website. I can set the MP160 as my default printer, using the command "lpr filename.txt" doesn't complain, and the command "cngpij -P MP160 filename" brings up Canon's little utility box, and (as with Eoghanalbar) when I push the print button on the machine it prints a blank page, but I can't actually print anything. Any ideas? Any info I've left off that could help? I've checked my cups logs; after the "cngpij" command above, they read,
```

localhost - - [21/Jun/2007:00:53:37 -0400] "GET /ppd/MP160.ppd HTTP/1.1" 200 11038 - -
localhost - - [21/Jun/2007:00:53:42 -0400] "POST / HTTP/1.1" 200 353 CUPS-Get-Classes successful-ok
localhost - - [21/Jun/2007:00:53:42 -0400] "POST /printers/MP160 HTTP/1.1" 200 672 Print-Job successful-ok

```
and show no errors.

---

### Post by imotlaw on 2007-06-22
Never mind, I figured it out; I checked the debug-level logs for cups, and it turns out that I hadn't done the "ln -S libtiff.so.4 libtiff.so.3" as I thought I had. That accomplished, everything seems to work. Thanks.

---

### Post by golebara on 2007-06-25
Hi,

I was searching for "How to scan with Canon Pixma MP160" and I came across this topic.

I'm using Ubuntu 7.04. When I initially tried to install the printer I went to openprinting.org and followed that same instruction. All of the commands worked and there was no error messages but the printer simply refused to print anything.

Then I went to System, Administration, Printing and removed MP160. After which, I clicked Printer, Add printer and since the printer is already plugged in (USB) and turned on, it found Canon MP160 (Canon MP160 USB #1) under the "Use a detected printer". I simply selected that one and clicked forward. I remembered something that I read on openprinting.org about using the MP150 driver so in the next screen I selected "MULTIPASS MP150" as the model and "High Quality Image (Gutenprint CUPS) (expert)" as the driver. After this point, I gave the printer a name and description and followed the rest of the prompts.

Now at this point, the printer has no problems printing documents. But I have no idea how to scan documents. I do not even know what applications/commands to use for scanning. Could someone please give me a hint? I noticed there is an application called "XSane Image Scanner" listed in "Graphics" but when I click on it, it says "No devices available".

Kind regards,

golebara

---

### Post by stadt on 2007-06-25
Canon provides drivers for printing and scanning. 

Get:

cnijfilter-mp160-2.70-1.i386.rpm
cnijfilter-common-2.70-1.i386.rpm
scangearmp-common-1.00-1.i386.rpm
scangearmp-mp160-1.00-1.i386.rpm

from: [http://www.canon-asia.com/index.jsp?fuseaction=support](http://www.canon-asia.com/index.jsp?fuseaction=support)

if you need some installation advice see 

[http://wiki.ubuntuusers.de/Canon-Drucker](http://wiki.ubuntuusers.de/Canon-Drucker)

Sorry the pages are in german, but I believe the relevant parts are understandable in english too

---

### Post by iladw on 2007-06-28
HI.

I've been using the gutenprint drivers for my PIXMA MP150 for quite some time.
It's is not perfect (compared with the original Windows drivers that they gave me on a CD) but it working. Well I didn't want to try the scanner because it is non-functional probably but the printer works.

Here's the link - [http://gutenprint.sourceforge.net/p_Download.php3]("http://gutenprint.sourceforge.net/p_Download.php3")

You can check the compatibility list but it's not listed there - no clue why. Probably they should update the web page or somethin'

Anyhow try installing it and don't fall for the "turboprint" crap :( Yes it works like a charm but it is commercial and the demo version puts a big colourful banner on each of your printed pages.

---

### Post by brn on 2007-06-29
Running Dapper.  I installed the recommended driver from [[COLOR="Navy"]openprinting.org[/COLOR]]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160") and followed the accompanying instructions.  I can print a document directly from **gedit** as well as images from **eog**.  But printing from **Open-Office, Acroread, Firefox, Thunderbird, LyX,** and even** lpr** *filename.txt* simply stalls.  In each case, **lpq** shows the file waiting in the queue but nothing happens from there.  Does anyone have an idea what could be wrong?

---

### Post by dotsi on 2007-07-02
I installed the printer as instructed but for some reason neither of my scanning software (scanning utility and XSane) doesn't recognize the scanner.

My /usr/lib looks like this:

```
ltpk@ubuntu:~$ ls -la /usr/lib/libtiff.so.*
lrwxrwxrwx 1 root root     21 2007-07-02 14:20 /usr/lib/libtiff.so.3 -> /usr/lib/libtiff.so.4
lrwxrwxrwx 1 root root     16 2006-10-25 01:42 /usr/lib/libtiff.so.4 -> libtiff.so.4.2.1
-rw-r--r-- 1 root root 335596 2006-08-08 11:53 /usr/lib/libtiff.so.4.2.1
```

Anything I can try?

---

### Post by dragonwings on 2007-07-14
[http://ubuntuforums.org/showthread.php?p=3017140#post3017140](http://ubuntuforums.org/showthread.php?p=3017140#post3017140)

---

