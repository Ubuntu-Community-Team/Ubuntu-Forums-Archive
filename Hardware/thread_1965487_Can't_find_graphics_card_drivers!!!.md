---
title: "Can't find graphics card drivers!!!"
date: 2012-04-25
forum: Hardware
---

### Post by DaimyoKirby on 2012-04-25
Help!
I have a Dell XPS 400; I recently wiped Windows Media Center Edition 2005 off of it, and installed Windows XP.

Now, I can't seem to find the drivers for the graphics card. I've searched everywhere, and no one seems to know what it is - it's lacking any sort of branding, and only has a few slightly distinctive numbers, which, when googled, have not turned up any successful results (at least, not that I can tell). If you still want to seem them yourself, let me know and I'll post them; I'm not right now since I don't want to have to shut my computer off and take out the card to read the numbers.

The last owner of this computer tells me that he doesn't believe the card was ever replaced.

Any help is greatly appreciated!

Additional Note: What I'm trying to do is play Minecraft. Whenever I run it, I get this error:
```

      Bad video card drivers!      
      -----------------------      

Minecraft was unable to start because it failed to find an accelerated OpenGL mode.
This can usually be fixed by updating the video card drivers.



--- BEGIN ERROR REPORT 7fe0271 --------
Generated 4/25/12 9:16 PM

Minecraft: Minecraft 1.2.5
OS: Windows XP (x86) version 5.1
Java: 1.7.0_03, Oracle Corporation
VM: Java HotSpot(TM) Client VM (mixed mode), Oracle Corporation
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Pixel format not accelerated
	at org.lwjgl.opengl.WindowsPeerInfo.nChoosePixelFormat(Native Method)
	at org.lwjgl.opengl.WindowsPeerInfo.choosePixelFormat(WindowsPeerInfo.java:52)
	at org.lwjgl.opengl.WindowsDisplay.createWindow(WindowsDisplay.java:185)
	at org.lwjgl.opengl.Display.createWindow(Display.java:311)
	at org.lwjgl.opengl.Display.create(Display.java:856)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:236)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Unknown Source)
--- END ERROR REPORT ffb29878 ----------

```
I doubt that helps, but I figured it wouldn't hurt to add.

---

### Post by Yellow Pasque on 2012-04-25
> **DaimyoKirby said:**
> I'm not right now since I don't want to have to shut my computer off and take out the card to read the numbers.

Pastebin your /var/log/Xorg.0.log
At the very least, look at output of lspci to see what video card you have.

---

### Post by Mark Phelps on 2012-04-26
You're asking about WinXP drivers, right?

According to Google, your PC has a Nvidia GeForce 7800 GTX video card.  So, you should be able to find XP drivers at the Nvidia site, or if the card is rebranded, at the suppliers site.

Have you tried using Windows Update after a hardware scan to find the drivers?

---

### Post by Yellow Pasque on 2012-04-26
> **Mark Phelps said:**
> According to Google, your PC has a Nvidia GeForce 7800 GTX video card.

I googled and found that different cards were available (including Radeon X600), so please wait for output from OP before advising.

---

### Post by houseworkshy on 2012-04-26
It's been a long while hazy while since I had xp, sp2, but it had some self diagnostics in the gui.  Sysinfo was one of them, in system tools or admin I think, there was also a hardware drivers bit in computer administration.   One could also test direct x. Those may tell you the card.  
If not you could try running a small linux distro live and installing sysinfo to ram, running that would tell you.  
If the machine can take it ramwise you could try running the latest knoppex live which may have the driver on it as it has most of the popular ones in it.  With luck that would not only tell you what is there but whether it works or not.

---

### Post by DaimyoKirby on 2012-04-26
[QUOTE=Temüjin]Pastebin your /var/log/Xorg.0.log
At the very least, look at output of lspci to see what video card you have.[/QUOTE]

Where exactly is that? Because that sounds like an Ubuntu file path.
Also, what is "lspci"?

[quote=Mark Phelps]You're asking about WinXP drivers, right?
According to Google, your PC has a Nvidia GeForce 7800 GTX video card. So, you should be able to find XP drivers at the Nvidia site, or if the card is rebranded, at the suppliers site.
Have you tried using Windows Update after a hardware scan to find the drivers?[/quote]

Yes, I am.
Well, I ran the Dell Support Center, and that did a run-through of my whole computer, and it threw up an error for the graphics card, as expected, saying that it needs the correct drivers. And I just checked the Microsoft/Windows Update, and there isn't anything about graphics cards listed for updates.

[quote=houseworkshy]One could also test direct x. Those may tell you the card. 
If not you could try running a small linux distro live and installing sysinfo to ram, running that would tell you. 
If the machine can take it ramwise you could try running the latest knoppex live which may have the driver on it as it has most of the popular ones in it. With luck that would not only tell you what is there but whether it works or not.[/quote]

I checked system info, and just like the hardware manager, the card is just listed as "video controller (VGA compatible)".
I've already looked in dxdiag, but it just says "N/A" for all the information about the card.
For now, I'd like to hold off with trying stuff with Linux, until there seems to be no other easier options.


I'm also considering just actually spending some money for once, and getting an upgraded graphics card. These are the two that I've found, and any thoughts/better suggestions are welcome.
[Asus ATI Radeon HD6450 Silence]("http://www.4allmemory.com/video-card/dell-xps-400/")
[Sapphire Radeon HD 5450]("http://www.amazon.com/Sapphire-Radeon-PCI-Express-Graphics-100292DDR3L/dp/tech-data/B004N3BH0C/ref=de_a_smtd")
(I don't really know if these are any good, I just found them almost by random, and they have good reviews and seem to be compatible)

---

### Post by houseworkshy on 2012-04-26
I've just searched for your pc and found [http://compreviews.about.com/od/maindesk/gr/DellXPS400.htm](http://compreviews.about.com/od/maindesk/gr/DellXPS400.htm) which includes default specs.  If it hasn't been upgraded then you have an ATI Radeon X300SE Graphics Card with 128MB Memory

---

### Post by DaimyoKirby on 2012-04-26
> **houseworkshy said:**
> I've just searched for your pc and found [http://compreviews.about.com/od/maindesk/gr/DellXPS400.htm](http://compreviews.about.com/od/maindesk/gr/DellXPS400.htm) which includes default specs.  If it hasn't been upgraded then you have an ATI Radeon X300SE Graphics Card with 128MB Memory

I looked for it on AMD's site, but I'm not sure which brand I'm supposed to choose, since there are no brand markings on the card itself. [[Link]]("http://support.amd.com/us/certified/graphics-cards/Pages/listing.aspx?c=ATI+Radeon%E2%84%A2+X300+SE")

---

### Post by houseworkshy on 2012-04-26
There is also [http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)  which has detect and install programs, could try one of those.  I think that as you own the hardware ( which the detect program will discover ) you shouldn't be charged for the driver.

Minecraft looks fun by the way and there seems to be a free classic version too.  As that one is older perhaps wine could run it from Xubuntu.

---

### Post by DaimyoKirby on 2012-04-26
I downloaded the program, but whenever I run it, it opens then closes, just barely flashing onto the screen.
(I know it works, since it detected a better driver for another card I had on this computer.)

Yeah, Minecraft is awesome; you don't need wine to run it, since it's a java-based program, and you can download a .jar version of the full game instead of the .exe.

---

### Post by QIII on 2012-04-26
Brand is not important.  ATI series is.

Start -> Run and type dxdiag

That should give you the info you need.  Post that back here and we'll help.

Be aware that both ATI and NVIDIA have "legacy" cards that need legacy drivers.

---

### Post by DaimyoKirby on 2012-04-26
Yeah, it doesn't recognize it.
[IMG]http://i.imgur.com/NrBlk.png[/IMG]

---

### Post by houseworkshy on 2012-04-26
I just got lost rambling round sites like abandonia.com looking for the free minecraft classic mentioned on wikipedia.  I didn't find it but there were so many pages of spam in my search results that doesn't mean it isn't there.  
The driver should be cross er ... manufacturer.
 
You may well be better going from the xubuntu side ( guessing you have it based on your sig ) and trying the hardware drivers to see if one is in the repros.  Be a lot less fuss.  
Wine ( a windows emulator which is in the repro's ) is pretty good on unsupported windows, like xp.
I like emulators, Dosbox is another good one.  Almost like my old computers are still there living as a tiny file in my new one.  Enjoy a bit of retro gaming from time to time. even spectrum stuff sometimes.
As to minecraft I did find a lot of play in the browser things, these can often be downloaded as .swf's and played offline.

---

### Post by DaimyoKirby on 2012-04-26
Well, I had a usb drive with an installation of Zorin OS on it, so I plugged it in, restarted, and booted into the LiveUSB.
It's incredibly fast! And aren't LiveUSB's supposed to be slower than a full installation?

Anyway, I looked into the Additional Drivers tool, and it didn't find anything. So I went to Minecraft.net anyway, downloaded the game, and ran it, and it worked perfectly!

So honestly, I don't know what type of card that is, and if there's some way to find out through Linux (terminal, maybe?), let me know, because it'd still be nice to know.

---

### Post by houseworkshy on 2012-04-27
There is though I don't know Zorin or what is in it's repositories so not sure what applies.  In Ubuntu one would install sysinfo "sudo apt-get sysinfo" entered in the terminal, then run it either from the link it puts in system tools or by entering "sysinfo" in the terminal.  That would ferret out system specs.  Your sig says Xubuntu so that would be the way in that.  As your friend says he didn't upgrade the card I think we've found out what it is, who made it doesn't matter much.  It could be the driver isn't supported anymore, I note some of them have been moved into some sort of archive.  You may be better off with an  open source driver anyway.   
As xp isn't supported going online with it is like going to sea in a sieve so you'd deffinately be better with a linux.  If you feel like splashing out RAM is the thing to buy before a card.  Whilst you could squeeze Unity or KDE on it's not really enough to simply run the OS;  you'll need room for the programs and apps to run as well.    
Even without extra RAM there a qute a lot which are very happy with 512 MB ram, Lubuntu may be a  good one, slitaz, there are a lot of fully supported versions out  there.  distrowatch.com is a good site for searching for them.  Lots of  threads here on what is best for lower spec machines.  But it's not that low spec, duel core at 2.8ghz, rather nice in fact, just a bit low on hd space and ram.  Could easily kit it out a lot better than "media center" ever was.  Short of hardware failure it could comfortably run fully supported modern systems fast and cool ( keep it clean ) for many years yet.
Enjoy the game.

---

### Post by Yellow Pasque on 2012-04-27
> **DaimyoKirby said:**
> So honestly, I don't know what type of card that is, and if there's some way to find out through Linux (terminal, maybe?), let me know, because it'd still be nice to know.

As noted, the terminal command is:
```
lspci
```

---

### Post by DaimyoKirby on 2012-04-27
Ahh, found it:
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```
So I have no idea why those drivers weren't working correctly, but Zorin runs it fine.

And yeah, it's all pretty decent; It seems that I may even qualify for the Skyrim minimum specs :-D
I have another radeon card that would work with my computer, a Radeon 9250. When I looked on [a comparison site]("http://www.gpureview.com/show_cards.php?card1=85&card2=305"), it seems to say that the 9250 is better, however I've had many issues with it in the past.
Anyone have any thoughts on this?

EDIT: Found this [[Link]]("http://www.tomshardware.com/reviews/best-graphics-card-gaming-performance,3042-7.html"), and when I *ctrl+f*'d for the x300, it was listed higher than the 9250, so I assume that means that it performs better?

But yes, although some of the initial hardware isn't that great, there's lots of room for upgrading, which makes me happy. I also very glad the processor is good, since those are expensive. I currently have 2.9Gb or ram installed, so I'm pretty good there (for now).

Zorin is super-fast, much faster than even Xubuntu or Lubuntu were, so I'm very impressed with it. It's still a little clunky in some areas (or so it seems to me), being younger than other distros (except for Lubuntu, maybe), but it's still very incredible; it's very similar to Windows, too, which makes me happy - the best of both worlds? :-)

---

### Post by Yellow Pasque on 2012-04-28
> **DaimyoKirby said:**
> the x300 was listed higher than the 9250, so I assume that means that it performs better?

Yes.

---

### Post by DaimyoKirby on 2012-04-28
Thanks so much everyone! Your help is much appreciated, and I even found my new favorite OS!

Thanks.

---

