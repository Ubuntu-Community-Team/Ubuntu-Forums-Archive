---
title: "after sudo scanbuttond still scan problem"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by ronny_d on 2007-08-08
Hi, 

I have bought a whole new and beautiful Canon Lide 25 scanner and according to Sane website it would work 'good' in my Ubuntu 7.04 Feisty Fawn, so please answer for this Feisty Fawn distro only. 

Before i had posted this thread:

[http://ubuntuforums.org/showthread.php?p=3096597&posted=1#post3096597](http://ubuntuforums.org/showthread.php?p=3096597&posted=1#post3096597)

to inform on Canon Lide 25 and so now i just tried a scan, the program 'xsane' starts fine, detecting my usb device perfectly, then i want to make a simple scan... and get black screen in preview mode as well as in other mode (out.pnm and can save in jpeg and so on), but everywhere black screen. 

Someone... out there... help me out. What is this unusual black screen and what must i do to solve this so my scanner Canon Lide 25 was not bought for nothing, i am however sure the scanner itself is perfectly well and i bought it all new and undamaged, nothing wrong with the scanner and usb plugged in, usb is 1.1 but that is fine with my 1.1 simple system. 


Ubuntu is most lovely, but finding out how things work instead of how things do not work is best of all. 


What is the solution so i can have positive scan results to do my work? Zillions of Thanks for solving this problem of black screen... Please... somebody help.

---

### Post by Al3xK3aton on 2007-08-08
A black screen is a common symptom of your monitor being turned off. If you turn it on then you should be able to see what you scan.

Also, check the contacts on your USB connection, if it's dirty then it won't work as well.

---

### Post by ronny_d on 2007-08-08
> **Al3xK3aton said:**
> A black screen is a common symptom of your monitor being turned off. If you turn it on then you should be able to see what you scan.

Also, check the contacts on your USB connection, if it's dirty then it won't work as well.

I am not that stupid. Please do no more reply on this level. 


You do not understand that the device is detected. 


Please only people with knowledge on this: reply.

---

### Post by Bachstelze on 2007-08-08
I have the same scanner, this is a known kernel bug in Feisty, A workaround is to use scanbuttond :

```
sudo apt-get install scanbuttond
scanbuttond
```

Then your scanner should work fine in Xsane. This bug is fixed in Gutsy.

---

### Post by ronny_d on 2007-08-08
I will specify some more. When you scan in xsane normally there is choice between preview or via "out.pnm" and save for example into jpeg, and so on. Now, when i scan preview gives "black" in its window (so not the monitor at all of course, come on!), and also when i scan "out.pnm" and save to jpeg or some format, it gives only black (so that is for example in the jpeg). Of course i have put 'that what i want to scan' on the scanner, so no more dumb jokes on "scriptkiddies level" or that sort of level on "monitor" or something, but anyway xsane shows 'black' as if nothing on the scanner, or as if i would have scanned black (but such i have not put on my scanner at all; instead: i put something very colourful on the scanner to be scanned).  I am very familiar with xsane, before i had an Epson 1200 Perfection scsi, but because now i have usb 1.1 system, i had bought this Lide and it must be a good scanner, for sure. So what about xsane and how to solve this problem. Please only people who know on this problem, answer.

---

### Post by ronny_d on 2007-08-08
> **HymnToLife said:**
> I have the same scanner, this is a known kernel bug in Feisty, A workaround is to use scanbuttond :

```
sudo apt-get install scanbuttond
scanbuttond
```

Then your scanner should work fine in Xsane. This bug is fixed in Gutsy.


Hey! Thank you. A kernelbug... (they shouldn't do that... ;-)...) 

I will try this sudo apt-get "fix" that you say. I like Feisty... and i hope Feisty will work fine very soon for all i need; i do not feel like upgrading yet to Gutsy, but thank you for the information and i am going to try first this sudo command out. 

Maybe i need reboot after the command? But i will try the sudo "fix" out anyway first and see if i can scan then.

---

### Post by ronny_d on 2007-08-08
> **HymnToLife said:**
> I have the same scanner, this is a known kernel bug in Feisty, A workaround is to use scanbuttond :

```
sudo apt-get install scanbuttond
scanbuttond
```

Then your scanner should work fine in Xsane. This bug is fixed in Gutsy.


I did this sudo and scanbuttond was announced to be installed succesfully. I rebooted because i had the same black screen/window/scan result and came back, but now... xsane cannot detect my device (comes with the (familiar?) list of about 7 reasons why not, like for example 'maybe device is busy', or something, and several other options why xsane cannot detect the scanner/device, ii checked the cables again) and i remember i once with my other scanner and former computersystem had this too, and i remember that there was a command how i solved it and after that xsane could scan for the devices again. I try to remember that command..., something in the option -L, but i forgot for now.  


What have i done so far? I forgot the command that had in its option 

-L

the option... i remember, but i forgot what the command was.


Then i downloaded 'scanimage'..., just did so, then i put on commandline scanimage or whatever it was, just did it, all of a sudden the scanner made a real noise, i guess it was scanning... but then... it rendered "funny signs" looking like @ allover in the xterm anyway the terminal... 


But... now we know for sure the device (scanner) is there! 


But so what is the command to force my scanner to scan with xsane /sane (probably not scanimage...) and not in some terminal but in the program so i can see what i scan and work with the result and so on?  


Do you know maybe how to solve this? Or does anyone know how to solve this? 


The scanner so functions. But it is about how to make 'sane / xsane' show my scans, but even now sane / xsane has to "admit" my scanner is there, it is well, but i forgot the command for this for now...

---

### Post by ronny_d on 2007-08-08
Now that the kernelbug was mentioned, i for example found this:


"Bug description [edit]

Binary package hint: libsane

In Feisty, using xsane or Kooka, my Canon Lide25 scanner, which uses the plustek backend, does not produce any scanned image, though both gui applications go through the motions (progress dialogs, etc) and produce a black preview. Using the command line 'scanimage' does produce a scan correctly

The scanner works correctly in Edgy.

Fix= disable "usb selective suspend/resume' in linux-source

ProblemType: Bug
Date: Thu Feb 15 22:27:27 2007
DistroRelease: Ubuntu 7.04
Uname: Linux feisty 2.6.20-8-generic #2 SMP Tue Feb 13 05:18:42 UTC 2007 i686 GNU/Linux"

i found it on the web, but i have a slightly different kernelversion, 2.6 but the rest is different.

Same scanner. 

But so i had a slightly different outcome: at first sane was giving black preview and black "out.pnm", jpeg, it made no difference, and then i installed the scanbuttond via sudo, as i was told, but then sane could all of a sudden not locate my device or how to say this, then... i  somehow downloaded with apt-get scanimage and tried out scanimage from commandline (without even having known about his quote i found on the web just now) and got the "@@@@" and so on result in the xterm / terminal only. Or now i see it are '?' in black, i don't know whether copy-paste will render the same as what i see here in my xterm:


&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;


In fact it is one string... that fills the entire surface of the xterm and that is what 'scanimage' scanned... via commandline...  Of course this was/is _not_ what i intended to scan at all and looks in no way like it.



So... how to make xsane or even scanimage detect my scanner and scan appropriately (both, as they are supposed to do)? 


I suppose scanbuttond as i did via sudo 

sudo apt-get install scanbuttond
scanbuttond

(though when i copy-pasted all this exactly in terminal, only 

sudo apt-get install scanbuttond

is given and immediately password prompt followed)

is good, but maybe something more is needed. I somehow cannot recall this command with option -L..., it was long ago and only once.


Sometimes... devices and software are not that logic at all and just sometimes they all of a sudden can work, but sometimes without any apparant reason, they refuse.  


How to make xsane render my scans properly? Or maybe scanimage, just any good scanprogram, though rather sane or scanimage. 


What was the command that has option -L if i remember well and showed my scanner was detected by if i remember well sane/xsane... 



Else: how to make sane/xsane and/or scanimage detect my scanner and scan appropriately now that we know the above mentioned?

---

### Post by ronny_d on 2007-08-08
Fine, just now the command i lost came to my mind again:


scanimage -L
device `plustek:libusb:001:012' is a Canon LiDE25 USB flatbed scanner


So, my scanner is there for sure and 'seen' by scanimage; why then scanned so inappropriate?

---

### Post by ronny_d on 2007-08-08
Now... that the command scanimage -L came into my mind again, i tried out xsane again... and guess what: it so 'sees' my device... and comes up and so i scan...  something that is far from black... but guess what: again all black .... outcome "out.pnm" or jpeg, no difference.


Are we back from where we started? Let me try scanimage now... and see whether it would scan again in a terminal... 


(i have _not_ rebooted!)


O no... In the terminal it again starts exactly the same:

P6
# SANE data follows
202 150
255


makes a horrible noise... and comes again with all this



&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;



covering the entire terminal surface and in no way it looks like what i have on my scanner to be scanned...



So how to solve this problem? I may have to post a new thread?

---

### Post by Bachstelze on 2007-08-08
The wird signs you see in the terminal when you run scanimage are normal. They are your image data in binary format ;) You must write it to a file :

```
scanimage > image.pnm
```

and when it's done scanning, you can then open the image.pnm file in GIMP. I'm reinstalling a Feisty right now, to see what I can come up with.

---

### Post by ronny_d on 2007-08-09
Hi,

I first posted the thread [http://ubuntuforums.org/showthread.php?p=3157782#post3157782](http://ubuntuforums.org/showthread.php?p=3157782#post3157782)
 named  'canon lide 25 scanner black screen no scan", and then i was told to download or what via 


sudo apt-get install scanbuttond
scanbuttond


which i did, although when i copy-pasted all of 

sudo apt-get install scanbuttond
scanbuttond

in the terminal, the terminal only gave 

sudo apt-get install scanbuttond
and came with the password prompt

o.k., fine: i get it... 

anyway: i apt-getted scanbuttond as far as i know succesfully... 

The poster who gave me the sudo-command informed me it was a kernel bug....


Then what? Here is an impression of what happened on my Feisty Fawn Ubuntu 7.04 usb 1.1 simplest system but i really, really like to solve this problem and be able to scan appropriately with my indeed new and good and beautiful scanner, please take a look:



Now that the kernelbug was mentioned, i for example found this:

QUOTE FROM THE WEB 
"Bug description [edit]

Binary package hint: libsane

In Feisty, using xsane or Kooka, my Canon Lide25 scanner, which uses the plustek backend, does not produce any scanned image, though both gui applications go through the motions (progress dialogs, etc) and produce a black preview. Using the command line 'scanimage' does produce a scan correctly

The scanner works correctly in Edgy.

Fix= disable "usb selective suspend/resume' in linux-source

ProblemType: Bug
Date: Thu Feb 15 22:27:27 2007
DistroRelease: Ubuntu 7.04
Uname: Linux feisty 2.6.20-8-generic #2 SMP Tue Feb 13 05:18:42 UTC 2007 i686 GNU/Linux"

END QUOTE FROM THE WEB


So i found that on the web, but i have a slightly different kernelversion, 2.6 but the rest is different.

Same scanner though.

But so i had a slightly different outcome: at first sane was giving black preview and black "out.pnm", jpeg, it made no difference, and then i installed the scanbuttond via sudo, as i was told, but then sane could all of a sudden not locate my device or how to say this, then... i somehow downloaded with apt-get scanimage and tried out scanimage from commandline (without even having known about that quote i found on the web just now and that i copy-pasted above...)  and got the "@@@@" and so on result in the xterm / terminal only. Or now i see it are '?' in black, i don't know whether copy-paste will render the same as what i see here in my xterm:


&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;


In fact it is one string... that fills the entire surface of the xterm and that is what 'scanimage' scanned... via commandline... Of course this was/is _not_ what i intended to scan at all and looks in no way like it.



So... how to make xsane or even scanimage detect my scanner and scan appropriately (both, as they are supposed to do)?


I suppose scanbuttond as i did via sudo

sudo apt-get install scanbuttond


is good, but maybe something more is needed. I somehow cannot recall this command with option -L..., it was long ago and only once.


Sometimes... devices and software are not that logic at all and just sometimes they all of a sudden can work, but sometimes without any apparant reason, they refuse.


How to make xsane render my scans properly? Or maybe scanimage, just any good scanprogram, though rather sane or scanimage.


What was the command that has option -L if i remember well and showed my scanner was detected by if i remember well sane/xsane...



Else: how to make sane/xsane and/or scanimage detect my scanner and scan appropriately now that we know the above mentioned?
__________________
Last edited by ronny_d : 29 Minutes Ago at 10:13 PM.
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
ronny_d
View Public Profile
Send a private message to ronny_d
Find all posts by ronny_d
Add ronny_d to Your Buddy List
  #9   Report Post  
Old 21 Minutes Ago
ronny_d ronny_d is online now
5 Cups of Ubuntu
	  	
Join Date: Jul 2007
Beans: 54
Lightbulb Re: canon lide 25 scanner black screen no scan



Fine, just now the command i lost came to my mind again:


scanimage -L
device `plustek:libusb:001:012' is a Canon LiDE25 USB flatbed scanner


So, my scanner is there for sure and 'seen' by scanimage; why then scanned so inappropriate?
__________________
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
ronny_d
View Public Profile
Send a private message to ronny_d
Find all posts by ronny_d
Add ronny_d to Your Buddy List
  #10   Report Post  
Old 15 Minutes Ago
ronny_d ronny_d is online now
5 Cups of Ubuntu
	  	
Join Date: Jul 2007
Beans: 54
Lightbulb Re: canon lide 25 scanner black screen no scan



Now... that the command scanimage -L came into my mind again, i tried out xsane again... and guess what: it so 'sees' my device... and comes up and so i scan... something that is far from black... but guess what: again all black .... outcome "out.pnm" or jpeg, no difference.


Are we back from where we started? Let me try scanimage now... and see whether it would scan again in a terminal...


(i have _not_ rebooted!)


O no... In the terminal it again starts exactly the same:

P6
# SANE data follows
202 150
255


makes a horrible noise... and comes again with all this



&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;



covering the entire terminal surface and in no way it looks like what i have on my scanner to be scanned...



So how to solve this problem? I may have to post a new thread?
__________________


So i posted this new thread... 


I love Feisty Fawn but i need to do my work... Even i have another new Samsung ML1610 that is not working either but this thead is not even on that malfunctioning... (the printer has a red light on on "On Line / Error" while being detected automatically and installed without problem, yet nothing..., i have no idea why it is not working, it is brand new, but this thread is not even on that.) 


So how to fix this bug (?) further in my Feisty Fawn so i can have good scan results and be able to at least do that part of my work? 

Please only reply for Feisty Fawn desktop version (no laptop; i am not sure, but who knows it makes a difference...) and only reply when you know how to go on after 

sudo apt-get install scanbuttond 

.... to maybe show what more i may need to do in Feisty Fawn desktopversion to make sane/xsane or scanimage make my scans o.k..... Thanks.

---

### Post by A-Sylum on 2007-08-09
dude make it shorter next time nobodys gonna reply to something like that. (less detail).
but i read something about black previews? if so than change the amount of rgb and brightness. I couldn't tell if you did actually install the thing. if you did post again. Are you using xsane? cause i might be able to help you

---

### Post by ronny_d on 2007-08-09
O wait... so many replies already while i was editing my thread... 

I first take a look then to all those replies.

---

### Post by Bachstelze on 2007-08-09
Threads merged.


Did you upgrade your system ? I just installed a fresh Feisty and did a full upgrade and no more black previews :)

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> The wird signs you see in the terminal when you run scanimage are normal. They are your image data in binary format ;) You must write it to a file :

```
scanimage > image.pnm
```

and when it's done scanning, you can then open the image.pnm file in GIMP. I'm reinstalling a Feisty right now, to see what I can come up with.


Wow... O.K. I try to change the binary format with that > sign... and see what comes out then.

---

### Post by A-Sylum on 2007-08-09
what happens sometimes for me is if i have like a printer or something with a usb connection it uses that instead of the scanner. try unplugging everything!
(except the printer)

are you running xsane on the terminal!?!?!?!?!

---

### Post by Bachstelze on 2007-08-09
> **ronny_d said:**
> Wow... O.K. I try to change the binary format with that > sign... and see what comes out then.

It doesn't change anything, it just writes the data to a file instead of displaying it in your terminal.

@A-Sylum > don't bother. This is a very well known issue and it is definitely caused by the USB suspend feature introduced in kernel 2.6.20. Running scanbuttond is the only known workaround for Feisty, besides recompiling the kernel.

---

### Post by ronny_d on 2007-08-09
I copy paste from my terminal from prompt on and there is a whole difference indeed: 

~$ scanimage > image.pnm
~$ 


(no binary images...)


But so now i try to find that file... huge file... image.pnm somewhere...  o.k., found it and open it with the Feisty version of Gimp... and now... i do not see any 'image'... like i know i have scanned, i checked... it is there on the glass, made a lot of scans like that before with my former scanner, the same "type" of image and scan, but... so maybe this is something of gimp... then, gimp in Feisty Fawn..., though i am not sure, i have Feisty only like one week..., very short and i have been hardly yet come to work, although i really like Feisty.... 


But so.... somehow maybe maybe... the scanner scans very small..., i am not sure,  but that that is why i cannot see it in gimp... I try it again with transparant background (in Gimp), so i can be sure because the 'scan' i want to make is definitely not transparant.  


No: the result (now we are talking of GIMP) is the same: it is white (and independent from background GIMP) but i cannot see what is on the white paper and it seems GIMP is representing the scanned image so very tiny, i cannot see... what is 'written' on it. 


Maybe i... try xsane/sane... again.  I call up xsane and it anyway recognizes my device.. (seems like a good start...) I scan 'out.pnm'... i do not do preview..., but immediate scan and see what comes of it "receiving RGB data'..., here we go again: BLACK screen again. 


So... What next? 


Upgrade another Feisty... Wait... I first read the other replies too. But until so far these were my tests upon your advice. O.K.: you install this same Feisty... like you say and then maybe comes the best solution. I will check the other replies now too.

---

### Post by ronny_d on 2007-08-09
> **A-Sylum said:**
> dude make it shorter next time nobodys gonna reply to something like that. (less detail).
but i read something about black previews? if so than change the amount of rgb and brightness. I couldn't tell if you did actually install the thing. if you did post again. Are you using xsane? cause i might be able to help you


I may not need you then... It for sure has nothing to do with your "brightness", A-Sylum...., so best for you is to not post again. You sound like... some... sticky stuff i really don't need and far from bright rgb.

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> It doesn't change anything, it just writes the data to a file instead of displaying it in your terminal.

@A-Sylum > don't bother. This is a very well known issue and it is definitely caused by the USB suspend feature introduced in kernel 2.6.20. Running scanbuttond is the only known workaround for Feisty, besides recompiling the kernel.


USB suspend function? Wo..., i am learning a lot here. Do you need my kernel? My kernel is 2.6 something, but i guess not 20..., though now i am not sure; i downloaded 'kernelversion' via commandline so as: 

~$ kernelversion
2.6

but it is too non-explicite for me; i wanted the full version to be seen but so "kernelversion" does not do so and i have to reboot then again... 

Do you need my exact kernel?

---

### Post by Bachstelze on 2007-08-09
Try that, then :

```
scanimage --resolution 300 -x 215 -y 293 > image.pnm
```

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> The wird signs you see in the terminal when you run scanimage are normal. They are your image data in binary format ;) You must write it to a file :

```
scanimage > image.pnm
```

and when it's done scanning, you can then open the image.pnm file in GIMP. I'm reinstalling a Feisty right now, to see what I can come up with.


O.K... Maybe you have reinstalled... the same Feisty Fawn Ubuntu 7.04 kernel 2.6.... 16 something... (i cannot get the kernelversion via command 'kernelversion', it then only says "2.6", but the other one is 2.6 .... 15 something; else i have to reboot...)


Yes: in Gimp... somehow... with scanimage via commandline 

scanimage > image.pnm


it so scans... but then you may want to open that file in GIMP... and then: can you see what you have scanned or... 

I do a test now with a very bright colour, far from white and far from black... but it is the same "result"... I guess it is 'nothing' but GIMP has another way of showing it is 'nothing' than the black screen of xsane....


Or?


So... the device is detected...; maybe the device (scanner) was not detected by xsane after the "black window surface", or how to describe that, result and so... xsane "next time" gave that my scanner was not found? Then so that may have called for usb suspend...; well maybe... Or the 'usb suspend' already was there... and caused non-synchronous "scans" or pseudo-scans resulting in "black screen" in xsane. Whatever the cause..., it is a problem that needs to be solved. 


Well, i will not forget about that particular look of  'binary code' in this issue.  ;-)

---

### Post by Bachstelze on 2007-08-09
> **ronny_d said:**
> 
I do a test now with a very bright colour, far from white and far from black... but it is the same "result"... I guess it is 'nothing' but GIMP has another way of showing it is 'nothing' than the black screen of xsane....

That's because for some reason, scanimage scans only a part of the image, and at low resolution. Use the command I told you above to scan the full image at a more decent res.

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> Threads merged.


Did you upgrade your system ? I just installed a fresh Feisty and did a full upgrade and no more black previews :)



No i did not upgrade my system, or now i am not sure what you mean with upgrade... I have some updates that i now see, 3 updates, so maybe just do that and then... But i guess i may confuse terminology, maybe. 


With upgrade you mean another Feisty Fawn or what do you mean exactly?

---

### Post by Bachstelze on 2007-08-09
Yep, the updates, that's what I meant. I say "upgrades" because I'm used to working in a terminal :p

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> Try that, then :

```
scanimage --resolution 300 -x 215 -y 293 > image.pnm
```


I do now this in a terminal. I remember in xsane, though if i remember well, in my former system, resolution was very, very high and out.pnm what it was called was always really huge

scanimage --resolution 300 -x 215 -y 293 > image.pnm
~$ 

I did not hear any scanner sound..., i will try again and not type in between in this browser, so the terminal is "focussed" on by this system somehow. So i repeat the command: 

scanimage --resolution 300 -x 215 -y 293 > image.pnm
~$ 


That made a whole difference, that is to say: it scanned rather a long time, really quite a long time, and i was almost afraid it would not stop and maybe burn, though it is not hot at all, but what a noise this scanner makes, but o.k., it is the first time for me with this type of scanner. 

So now... check in GIMP "right"? I... open the file image.pnm...  and yes: it is big, but... it is all white and does not look like what i intended to scan..., it is just... plain... but... maybe i see a difference (now that i at least can see some at all of a scan...)  on one of the... edges... of this image.pnm as if... the edge of the scanner was scanned, or... but i don't know how to send it to this forum..., but now i try to make it for example jpg and see what it will look like then (with this particular "smoked" 'edge', though that i say "smoked" has nothing to do with heat or fire, it is just a 'print' in the GIMP picture, that is: the result of this "scan", attempt to scan... 

O.K.: i see it is a huge file, size 2539 x 3460... I will do another try of it, exactly the same, and see if again the same result with that particular sort of "edge")


So again:

 scanimage --resolution 300 -x 215 -y 293 > image.pnm


and scanning took equally long, so that is the same. I open in my home directory the same file image.pnm with GIMP, in GIMP... and i see exactly the same result as the one before:

(huge file, as specified in commandline) white body and to the right... this particular edge, how can i describe it, it is "smoked", as if the scanner's lid, or what is such called (i am no native speaker but of course...) was a bit opened there, but it so was not (i checked) "in reality". So... what is this? 


Why don't we see the image we have put on the scanner's glass? And i have experience with scanners, i put whatever on my (former) scanner and it scanned, no matter how big, no matter how small, so... with all this now i almost start to doubt how i put the object that i want to scan is the cause of all this, but such cannot be true. 


I remember in xsane in my former system and with other scanner, i could put something small in the corner, then xsane made the huge file as aways (out.pnm) but always the thing i scanned was to be found back reasonably easy in the huge pnm (the thing / object i scanned was far smaller the size of the pnm is what i mean), and so that should work, but so now... this cannot be the cause that in GIMP nothing is to be seen but a peculiar edge alongside a white "body" (or how to name that). Though the inside of the scanner's lid is white..., the same white as in the GIMP's picture. 


I now will put something totally different on the scanner, its colour blue and very big... well... big enough so i cannot fully close the "lid" or cap or whatever it is named in English and do the test again, focus on the xterm:

 scanimage --resolution 300 -x 215 -y 293 > image.pnm

it really scanned, i saw its lights, it took some time again (huge file) and so now i check again in GIMP image.pnm... and it renders exactly the same "picture" as i described before with this peculiar edge... at one side. 


I guess it was not because of that i did not delete  the image.pnm each time i made a new scan, i suppose image.pnm should be overwritten with each scan.. because it is not like saved in jpg and so on, so that cannot be the cause of exactly the same "result" despite total different "things" on the scanner..., total different "scans" (but no scans). 

So: this is the result of the tests so far. 


The file became bigger and should be visible, but so that is not it. So what else could it be to solve this probable or real 'bug'? Rewrite the kernel via proc? I would like to do so if you tell me how and but of course whether such is a solution to this problem.

---

### Post by ronny_d on 2007-08-09
... Or i guess "image.pnm" is some sort of template; anyway: no result except bigger and therefore clear to see... no positive result of what was on the scanner at all yet.

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> Yep, the updates, that's what I meant. I say "upgrades" because I'm used to working in a terminal :p

I updated so. But... although i suppose that has nothing to do with it, recently i got stuck in installing Drupal 5.1 because of mysql and the sequence i chose of installation or maybe not at all the sequence was the cause, i anyway wanted to download Drupal only for my own machine, not for "outside" yet, so somehow... the installation did not work out and the database, must have been mysql,  could not be found and some other password i had to give and chose it to be 'randomly generated' caused the installation to fail, the message was that some error such and such was on, anyway: i tried to uninstall it, but now with every update it is coming back in an attempt to install itself but cannot and returns some failure or error message, but... as far as i can see this debian package or so, some configuration, is not related in that level to other updates (or i hope so), because all my other updates have nothing to do with Drupal. But so anyway i updated (but this with Drupal i only have since yesterday: that was when i tried to install it, then because of error and i had to configure by hand i wanted to uninstall it since remove did not work).

---

### Post by Bachstelze on 2007-08-09
So. I reinstalled a real Feisty - the previous attempt was in vmware - and I got the same problem as everyone : black preview in xsane. However, runnins scanbuttond *did* fix it, so *please* do just that. Firstly, reboot. Then, run scanbuttond in a terminal **as yourself**, that is, *without* sudo. And the, xsane definitely *should* work.

---

### Post by ronny_d on 2007-08-09
Originally Posted by HymnToLife  View Post
Threads merged.


Did you upgrade your system ? I just installed a fresh Feisty and did a full upgrade and no more black previews 


Yes, "threads merged" while i was trying to make a new thread, but so this works out too so far. I hope maybe rewriting the kernel, i hope this is possible via proc, for this particular issue can be an option. Though i would not know how to do that. Else update automatically via sudo. Or how come you, with the very same scanner, do not anymore have 'black screens' and such with the same Feisty... or is it another Feisty and are there updates for this Feisty to end this bug / solve this bug? Would that my new bought printer Samsung ML1610 gives 'On Line / Error' ("red light" that does not look good and it cannot print out testpage.. therefore) but driver was immediately recognized and installed like automatically, self-detected,  also have to do with this, what you called it, 'usb suspend function' (or what was it)? Both laserprinter and scanner are usb... Now i so wonder whether the printer may be also "suffering" from this usb suspend issue... Is such possible?  Since threads already merged, i keep it to this thread just for now. But could it be that also my usb printer is hanging on this issue?

---

### Post by Bachstelze on 2007-08-09
> **ronny_d said:**
> Or how come you, with the very same scanner, do not anymore have 'black screens' and such with the same Feisty... or is it another Feisty and are there updates for this Feisty to end this bug / solve this bug?

The same FEisty, but in vmware. When I installed it on a real computer, I had the black preview in Xsane too, bur scanbuttond fixed it, as it did for everyone else. See my last post.

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> So. I reinstalled a real Feisty - the previous attempt was in vmware - and I got the same problem as everyone : black preview in xsane. However, runnins scanbuttond *did* fix it, so *please* do just that. Firstly, reboot. Then, run scanbuttond in a terminal **as yourself**, that is, *without* sudo. And the, xsane definitely *should* work.


O.K. without sudo and no root, just ordinary user... "me",  i will try to run scanbuttond in a terminal from my home directory. O.K., i will reboot first... 

Yet i wonder: black 'preview'..., but did you get a 'real' scan (no preview mode) or...?


So i reboot now... and hope to come up with news lateron... as soon as possible. (I remember black screen caused by installing nvidia..., on another computer, but that is a whole different issue, not relevant, nothing to do with usb suspend either i suppose, but without any vision, screen or window, a computer is not... much at all.)  

I will reboot first and run scanbuttond from /home/myname in a terminal.... .. ....

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> The same FEisty, but in vmware. When I installed it on a real computer, I had the black preview in Xsane too, bur scanbuttond fixed it, as it did for everyone else. See my last post.

Hi... I so rebooted...
 
In your  post  you say: "So. I reinstalled a real Feisty - the previous attempt was in vmware - and I got the same problem as everyone : black preview in xsane. However, runnins scanbuttond did fix it, so please do just that. Firstly, reboot. Then, run scanbuttond in a terminal as yourself, that is, without sudo. And the, xsane definitely should work."


So i rebooted and gave in a terminal in /home/myname first 'scanbuttond' and got a prompt back, i was not sure and then i typed ./scanbuttond... then got bash "reply" and then did again scanimage -L and received prompt back:

:~$ scanbuttond
:~$ ./scanbuttond
bash: ./scanbuttond: No such file or directory
:~$ scanimage -L
device `plustek:libusb:001:004' is a Canon LiDE25 USB flatbed scanner
:~$ 

Then i started xsane and no problem scanning my device..., i scanned... now the out.pnm is... white.... while there is definitely a colourful postcard at the scanner..., but so that was a 'scan'... and now test this in 'acquire preview'...: it is... white... BUT... with some "vague stripes" allover the white "body", vertically... and looking like the computercode on products price tags and so on as everywhere nowadays, sort of purple haze... but vague.


But no more black though! 

When i do 'locate scanbuttond' in xterm, i see in all 'scanbuttond' files for backends resembling my scanner's backend for example:

backend_plustek.so.1.0.0
backend_plustek_umax.so
backend_plustek_umax.so.1.0.0
backend_plustek.so.1
backend_plustek_umax.la
backend_plustek_umax.so.1


but have no idea yet whether any of these relates to my specific  scanner
plustek:libusb:001:004

(i do not see that in scanbuttond files) 



In the scanbuttond via /etc 
i see buttonpressed.sh 
initscanner.sh
meta.conf


But so now... no more black previews... (!)... but... 

white... 

but in that "white body"... it shows (in preview mode) 

those vague purple haze vertical stripes.


What next... ????


(sigh...)


yet i love ubuntu

(but so far my new scanner and new printer somehow do not function... and it is the question whether for both this is due to 'usb suspend' kernel bug issue...)


So what next, now that the result changed. 


Do i have to do the command 'scanbuttond' in a different way from commandline in my "pwd"... home maybe? 


I hope to receive your answer soon.  I am looking forward to how this problem could be really solved. Thank you, really, for your help so far so i am not here out on my own with this, being no computerscientist at all.

---

### Post by ronny_d on 2007-08-09
CORRECTION

(i mis-copypasted, but this is the "true" copy-paste)

~$ scanbuttond
:~$ ./scanbuttond
bash: ./scanbuttond: No such file or directory
:~$ scanimage -L
device `plustek:libusb:001:004'

---

### Post by ronny_d on 2007-08-09
Anyway, i hope the 'correction' i gave for my commandline scanbuttond was received o.k., also i changed it in the "original post", so both now must look the same. 


Not that i am going to change that now (i do not dare to do that in "this phase" of confusion about the kernelbug), but... could it have something to do with the 'settings' in the xsane program? Or no...: such has nothing to do with 'usb', i see. :-P


If all this kernelbug 'usb suspend' would be solved, i guess i would feel really well. I know linux is a powerful OS (kernel, /gnu/linux, whatever they want to call it in whatever context). 

Are there maybe other "premises" you need to know about my Feisty Fawn here?

---

### Post by ronny_d on 2007-08-09
instead of 'kernelversion' uname:  2.6.20-16-generic


I will reboot again and try again run scanbuttond from userlevel, just immediately

---

### Post by ronny_d on 2007-08-09
After i rebooted and gave at the level of my home directory in xterm

scanbuttond


then started up xsane... preview... white... with vertical stripes of some "unidentifiable" colouring; stripe pattern look like price tag computer code as in shops nowadays. 


:popcorn:

Yet no more black. 


When i scan (no preview), the result is exactly the same as preview. 


Is there a solution for this?  


(And i am also here with a usb-printer ML1610 samsung brand new... red light on "On Line / Error", yet detected... and wonder about the connection but have no clue) :popcorn:

---

### Post by ronny_d on 2007-08-09
:popcorn:

---

### Post by ronny_d on 2007-08-09
> **HymnToLife said:**
> The same FEisty, but in vmware. When I installed it on a real computer, I had the black preview in Xsane too, bur scanbuttond fixed it, as it did for everyone else. See my last post.

Yes, for me too: it yet turned into white for me (with those funny vertical stripes),

but you said: "Did you upgrade your system ? I just installed a fresh Feisty and did a full upgrade and no more black previews "


What do you mean with a fresh Feisty? Is there another Feisty? What do you mean? :popcorn::confused:

---

### Post by ronny_d on 2007-08-10
ps -aux, there it is, i suppose:


root      1935  0.0  0.0      0     0 ?        S<   00:35   0:00 [ksuspend_usbd]


:popcorn::popcorn::popcorn: Maybe i have to get myself a new kernel for this...:popcorn:

don't know how, yet... :popcorn::popcorn::popcorn::popcorn:

i like to stay with Feisty, at least for a while because it is such a short while ago i only started; in fact hardly started...

---

### Post by ronny_d on 2007-08-10
I found this evaluation on Ubuntu on the web:
"For laptop users, working suspend is a make-or-break feature. If it doesn't work, your laptop becomes remarkably less useful. A substantial fraction of laptop users has trouble with the default swsusp suspend method and/or with ACPI suspend-to-ram. If we want these folksto use ubuntu, we need to help them use one of the other methods and/or ease customization of the current default methods."


But it could be said that this is equally true for 'desktop'/pc users, although then the suspend function seems to be in comparison to laptop users of opposite need.

CONCLUSION
I so have bought a scanner and printer for nothing, i cannot use it under Ubuntu Feisty. So i am in need of another kernel and i have not yet decided which Linux flavour, or maybe Apple.

---

### Post by ronny_d on 2007-08-10
Originally Posted by HymnToLife  View Post
"So. I reinstalled a real Feisty - the previous attempt was in vmware - and I got the same problem as everyone : black preview in xsane. However, runnins scanbuttond did fix it, so please do just that. Firstly, reboot. Then, run scanbuttond in a terminal as yourself, that is, without sudo. And the, xsane definitely should work."



But.... IT IS TRUE WHAT YOU SAY... ! :KS


scanbuttond WORKS...


My scanner Canon Lide 25.... IS WORKING PERFECT.... it is true!!!!!!


:):KS:):KS:KS:KS


THANK YOU.... 



GOOD NEWS... !!!!!!!!!!!!!!!!!!!!!!!! 


PROBLEM SOLVED WITH scanbuttond.... !!!!!!!!!!!!


I am all happy because of this :KS

---

