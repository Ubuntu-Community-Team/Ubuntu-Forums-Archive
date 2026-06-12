---
title: "Reviving an old desktop: HOW??"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by anil_robo on 2006-04-19
I just got hold of an archaic desktop yesterday (Acer Aspire) . My neighbor was moving and she had this old computer she was willing to throw in trash. I asked for it, and she gave it to me. I asked "how much for it" and she said "free" :mrgreen:

Poor girl does'nt realize the power of an old computer! Anyway she was so nice to have gifted me this wonderful legacious computer.

Issues:

1.Now this wonderful legacious computer comes loaded with win98, which I'll soon replace with a GNU/Linux distro. Which one? Should be small enough to fit 1GB hard disk, and still leave enough space for my files.

2. How much memory upgrade should I make? And how do I know which memory (SD RAM or other) should I have? DDR won't work I believe :rolleyes:

3. No USB, not even an ethernet card! Just an internal modem. Worse - it has a single free PCI slot (other one is taken by the sound card). I may chuck out the sound card, and have two free PCI slots. Any ideas about some ethernet cards/USB Cards that the motherboard and Linux may support?

4. What should I use it for? Well, I have two ideas as of now. I can place it in my living room, and hide the CPU - the monitor would display a slideshow of my family photos (and possibly videos). Another idea : I can use it as a file / web server. How well is such an old machine expected to perform as a web server? (I plan to host simple websites).

Thanks!

P.S. Machine specs:
Pentium 166MHz
72MB RAM
1GB HD
Working CD ROM drive
NO ethernet/WiFi
No USB
56kbps internal modem

 		 	 		 		 		 		 			 				________

---

### Post by IYY on 2006-04-19
The distro would have to be Damn Small Linux. It fits in 50 MB, can run on a system with as little as 16 MB of RAM. And it's based on Debian, just like Ubuntu!

---

### Post by Jagot on 2006-04-19
Another possibility is Puppy Linux:

[http://www.puppylinux.org/](http://www.puppylinux.org/)
[http://www.puppyos.com/](http://www.puppyos.com/)

---

### Post by anil_robo on 2006-04-20
Okay, so distro would be either DSL or Puppy. I'll choose based on reviews. 

**Issue1: Hardware compatibility:**

In the meanwhile, I have ordered some peripherals from buy.com. These are:

1. **USB Card**: Startech 2 Port Easy install USB PCI Card Adapter Pc Mac Plug AND Play
2. **Ethernet**: D-Link DFE 530TX Plus - Network adapter - PCI - EN, Fast EN - 10Base-T, 100Base-TX - 100 Mbps

Based on wiki.ubuntu.com, I checked for the compatibility of these hardwares and they appear to be supported out of the box. However, things may change with distro - and I am realizing I should have checked their compatibility with Puppy or Damn Small Linux. If someone has experience with these hardware pieces and linux, please let me know.

**Issue 2: How much RAM?**

I plan to use this old machine as a web server - no big websites, but just small HTML pages for informative websites. Will 72MB RAM be enough for this purpose? Does anyone have some experience with apache on such a low RAM?

Thanks -- Anil

---

### Post by Tom Tiger on 2006-04-20
Hmm.... a bit more ram couldn't hurt, if you can get more ram use it

---

### Post by goatflyer on 2006-04-20
Definitely Puppy over DSL.  DSL is so fixated on being able to fit inside 50MB that it cuts out way too much useful software, imho.  Just because a computer is old doesn't mean you have to limit your choice!

Puppy has its own unique package management system "dotpup" which has a respectable repertoire of software that runs on old machines, but for something more debian-ish (like ubuntu) you might try FeatherLinux (a very zippy Knoppix/Debian distro)

(EDITED to add:)
All distros should recognize your Ethernet card, but you'll have to experiment with USB.

P.S my smallest clunker is a P1 133 with 32MB ram.  I used the disk tools on Feather to create a swap partition to be able to get better performance out of puppy.  Dillo rocks on old machines.

---

### Post by anil_robo on 2006-04-20
The USB card and Ethernet card are delivered 2 hours back. I have opened the machine and installed both in it successfully. BUt... I did that in Windows 98. I want to boot with puppy linux bootable CD... but the sucker won't boot from CD!

I know it's not set to boot from CD, so I want to get into its BIOS to change 1st boot device to CDROM. But contrary to what the manual says, pressing Alt+ctrl+esc doesn't take me to BIOS. In fact, this key combo doesn't do anything at all!!!!

Does someone know of a way as to how can I boot from the CD in such case?

(P.S. - Or it'd be fine if I can boot from USB stick too - the USB card works fine. But... USB booting may not be supported by the motherboard - too old, 1997) :(

---

### Post by towsonu2003 on 2006-04-20
check out this link for choices of distro:
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

as for the key for bios, try googling w keywords:
bios <maker> <model>
or similar

---

### Post by Sef on 2006-04-20
> But contrary to what the manual says, pressing Alt+ctrl+esc doesn't take me to BIOS.

Usually, you just push one button to get into the BIOS.  Most often they are ESC, F2, and Delete.

---

### Post by anil_robo on 2006-04-25
Okay, I have made little progress.

As I said, I have installed the USB and Ethernet cards, and have done some testing if this machine can serve files on the internet.

I have installed apache on windows98 on this old machine, and can transfer files on intranet using IP address at about 100kbps. That is an excellent transfer rate I guess. So I conclude that this lowly machine WILL function WELL as an http server.

Now the question is, how to install Linux in it? It won't boot from CD or USB, and I can't get in the bios!!!

Could floppy drive be the answer? How do I install Linux (Ubuntu, Damn Small or Puppy) on this machine through a floppy? Or can I install through network? How can I install through network?

---

### Post by Zimmer on 2006-04-25
BIOS Issues
Unable to Access BIOS

Use CTRL-ALT-ESC to access the BIOS setup, the machine seems not to respond, putting a small key in the top left of the screen. It's actually Acer's way of asking for a password, on older Win 95 machines, this is ACERUK, but on newer machines (ie MMX, PII) it is ACERNWE.

If you get the password wrong three times though, it will lock you out of the BIOS altogether. Check the Acer motherboards section of this site to find the correct jumpers/switches to clear this.
No "Advanced" Section in BIOS

On some of the Acer Acros PII machines, in the BIOS there is no "Advanced" section (contains among other things the port settings) listed on the first screen. To access this you need to press the F8 key at the Main Menu.

[http://www.uktsupport.co.uk/acer/faq/acer.htm](http://www.uktsupport.co.uk/acer/faq/acer.htm)

---

### Post by confused57 on 2006-04-25
If you have a floppy drive, you can try Smart Boot Manager:

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

### Post by anil_robo on 2006-04-26
[quote=Zimmer]BIOS Issues
Unable to Access BIOS

Use CTRL-ALT-ESC to access the BIOS setup, the machine seems not to respond, putting a small key in the top left of the screen. It's actually Acer's way of asking for a password, on older Win 95 machines, this is ACERUK, but on newer machines (ie MMX, PII) it is ACERNWE.[/quote]

Thanks for the info and the link, Zimmer. However, it doesn't work. I pressed ctrl+alt+esc and the machine appeared not to be responding. I then typed these passwords and pressed enter. However, the computer starts booting windows 98 instead of taking me into the BIOS!

What's going on?? ](*,)

---

### Post by Zimmer on 2006-04-27
Well, : If the system displays the Acer Splash Screen, once you hear the beep, you should begin pressing CTRL+ALT+ESC. You may need to press CTRL+ALT+ESC continuously until you access the BIOS setup screen.
Or hold the CTRL+ALT and furiously bash the ESC key repeatedly to gt the timing right..took me ages to get into the BIOS of the old kit I tried this with.
So, if you have already worn the writing off the ESC key it might be time to research the motherboard and fiddle with jumpers to reset the BIOS (not for the fainthearted  - not even me - but then this was a free machine, right?) 
[http://www.uktsupport.co.uk/acer/mb/acermb.htm](http://www.uktsupport.co.uk/acer/mb/acermb.htm)
Can help you no further than giving you the link..
However, my experience with the old kit of a 233mhz Pentium 92mb RAM and an Orchid 3D card was like swimming in treacle. I did manage to surf the net with Dillo but the paint program froze the machine and the mouse movement was awful. Itried to use GeexBox on it as a last resort, but it just froze...as I was reformatting the disk to put W98 back I knocked the table and a vicious noise resembling worn out HDD bearings was heard, continuously.
So, anyone want some salvaged 72pin EDO RAM ?

---

### Post by anil_robo on 2006-04-27
[quote=Zimmer]..took me ages to get into the BIOS of the old kit I tried this with.
[/quote] Well, I have done it.
I made a bootdisk of smart boot manager using rawwrite, and then booted off the floppy. The floppy then asked me which device I want to boot with. Then I put in CD of Puppy Linux, and I was in Puppy moments later!!! :)

However, puppy couldn't recognize my D-Link ethernet card. So I'm back on Windows 98 running apache. Here is the link: [http://stooge.myftp.org]("http://stooge.myftp.org")

In my opinion, windows 98 works "faster" than puppy on this machine. However, I don't like windows98 that much. Windows 95 was much better! :)

Anil

---

### Post by confused57 on 2006-04-27
I've used Puppy Linux, but had to activate my D-Link ethernet card to access the internet.  It's pretty easy to do, I don't remember exactly how; but try clicking on System, Utilities, Tools or whatever it is, until you see the Internet(or Network) option.  May take a couple of tries, but I got it to work on my system.   I believe there's an option to install  a driver for various ethos cards, including D-Link, then a button to test the ethos connection.  Also, there's a Pup001 Zip file you download from the Puppy site that you can install a Pup001 file to the Windows root drive that will remember settings when you finish your Puppy session.

---

### Post by oyvindaa on 2006-04-28
[QUOTE=anil_robo]
2. How much memory upgrade should I make? And how do I know which memory (SD RAM or other) should I have? DDR won't work I believe :rolleyes:
[/QUOTE]

You could run Everest Home in Win98 to clarify what type of RAM your computer is using.

I still haven't found any program for finding out things like these in Linux :(

---

### Post by anil_robo on 2006-04-29
[quote=oyvindaa]You could run Everest Home in Win98 to clarify what type of RAM your computer is using.[/quote]
Thanks for the tip. The link is here: [http://www.softpedia.com/get/System/System-Info/Everest-Home-Edition.shtml](http://www.softpedia.com/get/System/System-Info/Everest-Home-Edition.shtml)

> I still haven't found any program for finding out things like these in Linux :(
There will be such a program, always! It's just that we don't know! :)
I googled, and came up with partial answers:
[http://www.memtest86.com/](http://www.memtest86.com/)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
And this: [http://hardware.newsforge.com/hardware/05/01/25/2034227.shtml?tid=126&tid=125](http://hardware.newsforge.com/hardware/05/01/25/2034227.shtml?tid=126&tid=125)

I think the command "lspci" would do this for you! :-k

---

### Post by anil_robo on 2006-04-29
[quote=confused57]I've used Puppy Linux, but had to activate my D-Link ethernet card to access the internet.  It's pretty easy to do...[/quote]
My ethernet card is D-Link DFE 530TX Plus, not D-Link DFE 530TX. The "plus" card uses a  different chip than the "regular" card, and this chip is not recognized by puppy.

I reached the [manufacturer website]("http://support.dlink.com/products/view.asp?productid=DFE-530TX+"), and it does contain the driver for my card. However, it's a "C" file and I dont know how to install it. The website lists instructions for windows driver installation, but not for Linux (where they are most needed) :confused:

Can someone tell me how to install a driver that comes from a c file?

---

### Post by confused57 on 2006-04-29
My ethernet card is D-Link  DFE-530TX+, which is pretty similar to yours.  In fact, I'm posting this  from Puppy Linux LiveCD.
I went back through how I configured my ethernet connection while I was on Puppy:
Setup----Ethernet/network wizare---Load Driver(I just used the top D-Link entry, seemed closest to what I had)---Auto DHCP(depends on your ISP)---Test etho.

Puppy will run pretty slowly from the LiveCD with low memory, but would be much faster installed on HD.

Hope this helps.

---

### Post by anil_robo on 2006-05-04
[quote=confused57]My ethernet card is D-Link  DFE-530TX+, which is pretty similar to yours.  In fact, I'm posting this  from Puppy Linux LiveCD.
I went back through how I configured my ethernet connection while I was on Puppy:
Setup----Ethernet/network wizare---Load Driver(I just used the top D-Link entry, seemed closest to what I had)---Auto DHCP(depends on your ISP)---Test etho.[/quote]

I tried the same thing with Puppy - but my card does not work! :(

I now know one more addition to my card specs: It's D-Link DFE 530TX + **Rev.F**

Can it get any better :-x

---

