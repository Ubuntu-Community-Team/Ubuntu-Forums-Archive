---
title: "Streaks appearing in scanned photos"
date: 2008-08-21
forum: Hardware
---

### Post by mawlinux on 2008-08-21
I am just one step away from ditching Windows completely at home, but this nagging problem might hold me back.

I'm doing a "One Month with Linux" series on my blog and some folks are watching to see how it works out for me.  I want to say at the end of August, "I made the switch."

I am seeing color-streaked scans in 64-bit Hardy Heron (Ubuntu 8.0.4) that came through flawlessly on **all exactly the same hardware in Windows**, and in 32-bit Hardy Heron on the PC I used as my Ubuntu testbed (and for my "[Ubuntu After One Week]("http://blog.markwill.com/2008/08/07/ubuntu-after-one-week")" post).  So, I know the scanner is not the problem, and Ubuntu in general is not, either.

[IMG]http://www.markwill.com/test/bad_scan.jpg[/IMG]

It happens whether I use xsane or kooka.  There must be some driver piece I'm missing on this 64-bit install.  It is an HP 3500c, just FYI.  Another difference is that I ran Ubuntu Studio on the 32-bit machine, which might have put a different driver in there.

The only hits I found on a similar situation were for a different scanner, but the "fix" was when the guy hooked it to a Mac instead of a Windows PC, so he suspected the driver.

Can anyone please help?

---

### Post by pytheas22 on 2008-08-21
I'd suspect a driver issue as well.  It may help to download [hplip]("http://hplip.sourceforge.net/downloads.html") (the HP printer/scanner driver) source and compile it--you will get a later version of hplip than that which comes bundled in Ubuntu.  It's easy to compile if you use the "automatic installer."

You could also perhaps try installing 64-bit Ubuntu studio (or at least the live CD) just in case it uses a different printer driver (although I doubt it does--the difference is probably between the 32 and 64-bit builds of hplip).

If that doesn't help, please let us know and we can look at other solutions.

---

### Post by mawlinux on 2008-08-21
Thank you so much for the reply.  I guess part of my problem is that I don't really know about compiling things.  I did download the latest version of HPLIP, because according to Synaptic I had an older version (like you said I probably did).

I ran the installer and chose "Automatic."  Your wording seemed like that would compile it for me.  It never asked about scanners, but when it asked about printers, I took the options appropriate for a networked printer (I do not have a USB-attached printer).

I performed a scan and got the colored lines again.

I tried to start the HP Device Manager but it never came up.  I will reboot and try again.

---

### Post by mawlinux on 2008-08-22
I rebooted and still I don't see the HP logo (near the volume icon at the top of the screen) that I usually see when booted into Ubuntu 8.0.4 (pretty sure I saw it in 32-bit and 64-bit).  Also, when I click on the HP Device Manager icon in the Applications | Accessories menu, I get nothing.

Xsane sees the scanner as an HP 3500c, but the scan again came out with the colored streaks on my final scan. Oddly, in the preview window after the Acquire Preview scan, it does not show streaks.

---

### Post by pytheas22 on 2008-08-22
Sorry that compiling hplip doesn't help.  It is interesting however that you mention that the scan preview doesn't have the blemishes.  Do you see blemishes in the XSane image after you perform the actual scan, or is it only in the output file?

If it's only the output file, then I'd suspect that it's a problem with the way that's being rendered, not the scan itself.  Have you tried saving in other file formats?

I'll also do some searches when I get a chance to see if that turns up anything about this problem on your scanner.

---

### Post by mawlinux on 2008-08-22
Yes, that's how it looks in Xsane's window after the final scan.  Thanks very much for you input thus far.  I'm trying to make Linux work for me this time, and this type of device support is what drove me away last time.

---

### Post by pytheas22 on 2008-08-22
I googled around a bit and have a couple of things you might try.  First, in XSane preferences, disable the "Enable Color Management" option.

Second, can you scan correctly by opening the GIMP (Applications>Graphics menu) and going to File->Acquire->Xsane->Device Dialog?

Also, it may help, if you haven't already done so, to install all of the sane backend stuff (by default it's not all there).  Run:
```

sudo apt-get install sane
```

After that, restart the machine and see if anything changes.

Installing the whole sane package will also add a third image-scanner program called xscanimage (you will have to call it from the command-line) that might give you better luck.  Probably not, but it's worth a shot.

Please let me know if any of this stuff helps.

---

### Post by mawlinux on 2008-08-23
Thanks so much for your time working on this with me.

Without making any changes, I went into GIMP as you suggested (I had tried that before, but it was worth a shot after I downloaded and used the update option for Ubuntu Media (one of the suggestions I had read).  Running Xsane standalone after that update had produced a streaky scan (color management was not enabled).

From Xsane within GIMP, a atreak-free scan resulted.  After closing GIMP to try xsane standalone, and then coming back and trying from GIMP again, it was streakier than ever.

Also from GIMP, I used Acquire, and then QuiteInSane plugin.  That produced a streakless scan, but very dark and not fixable through the Curves method.  I am quite familiar with adjusting photos both at the scanning stage phase at the post-production phase, and this was just not good enough to do anything with it.

I ran the command you suggested and rebooted.  Then I tried standalone xsane and it was very dark but not streaky.  Then I tried xsane from GIMP and it was the same.  Next, I tried the QuiteInsane plugin, and it produced a very streaky, very dark image.

So, there's no consistency to the results.

I've never had results like this with this scanner in Windows.  Hmmm... off to try the other suggestions you had.

Once again I'm leaning toward leaving Linux behind.  I work with computers all day in my job and I want to come home to a computer that works when I need it to for what I need, without having to go out and buy a bunch of "known good" devices for Linux.  But, I'm willing to put in a little more time.

---

### Post by 73ckn797 on 2008-08-23
This may not help but I encountered streaks on regular text document scans using X-sane. I adjusted the resolution to 200dpi and that eliminated the streaks. I have not scanned any photos as of yet. I used a HP Officejet 5610 with the latest drivers. It works in both the 64 & 32 bit versions.

I assume that you tried that already but felt like saying it anyway.

---

### Post by pytheas22 on 2008-08-24
I'm sorry that none of the suggestions helped.  The only other thing that I can say is to play around with all of the preferences in XSane to see if anything makes a difference.  Or you could switch back to 32-bit Linux, where the scanner works flawlessly, right?

You may also want to make a [support request]("https://launchpad.net/hplip") to the hplip people, who will know more about this than us.  One of the nicest things about the Linux development model is that end-users can easily communicate directly with developers to get problems fixed.

---

### Post by mawlinux on 2008-08-24
73ckn797, thanks for the reply.  I dropped it to 200 dpi and that got rid of the streaks, except a single green one.  The scan still looks really bad otherwise -- the color's wrong and it's very dark.  Even if I adjust the gamma or other settings, it looks weird.  Hard to describe.  It almost looks like a painting effect has been applied or something.

I might keep playing with it.  The funny thing is, I'm becoming obsessed over it even though I can count on one hand the number of scans I've done with this scanner in the past three years.  I was just hoping to make the change and be able to get rid of my Windows partition on this computer.  I'll always have at least one Windows PC in my house just because of my job and because family and friends call me for support, so I can just hook the scanner to that when I need it.

pytheas22,  Thanks again for all the help.

---

### Post by pytheas22 on 2008-08-24
> The funny thing is, I'm becoming obsessed over it even though I can count on one hand the number of scans I've done with this scanner in the past three years.

Yeah, I think a lot of us have this kind of experience with Linux.  You know that there's an easy enough workaround to your problem, which isn't life-threatening to begin with, but you become obsessed with making it work perfectly.

Anyway, I wanted to post again because another option that you might try is to run a virtual machine inside Ubuntu using VirtualBox or VMware.  Depending on how the scanner works (it's over the network, right?), you could access it directly from your virtual machine, which should make things work.  I'm not positive that this would work, and if the scanner is connected via USB it might be more difficult (but still possible, as I think that VirtualBox at least can access USB devices directly, without going through the host operating system, now) but it's worth a try.  In any case a virtual machine running XP is not a bad thing to have on hand for when you need to run a Windows program that doesn't work well in wine.

---

### Post by mark bower on 2010-02-04
I get two narrow streaks using Xsane with HP scanjet 3970, using Ubu 9.04 and 9.10.  I have tried nearly all the suggestions posted, and no luck.

What is really frustrating is that one cannot pinpoint a flatbed scanner (they are becoming more rare) that will work out of the box with linux(Ubuntu).  I have looked at the Xsane site and it doesn't seem to help - althoh the extensive work is appreciated.  Further, I really like a couple of the features provided in Xsane that are not available in the HP XP software that came with my scanner.  But the two streaks make use of Xsane impractical.

Would it be true that manufacturers do not write drivers for linux because there are too many desktop versions, ie, the linux community shoots itself in the foot by having so many desktop versions?  I can see no reason why they should be beholding to only windows and MAC?

mark

---

### Post by mark bower on 2010-02-06
In Xsane I had not selected the correct scanner in Window>Advanced Options>scanjet 3970.  When I selected the correct scanner, the streaks went away.

However, the quality of Xsane outputs is reduced compared to the output of the supplied HP scanware.  The difference is not trivial, easily noticed, and thus makes Xsane a poor choice.  I tried a number of different settings, but could not bring the quality of the Xsane output up to that of the HP software.

This forces me to stick with XP and the HP software.  Sad

mark

---

