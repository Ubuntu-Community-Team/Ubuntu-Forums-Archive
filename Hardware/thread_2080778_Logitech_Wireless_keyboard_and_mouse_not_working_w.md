---
title: "Logitech Wireless keyboard and mouse not working with 12.10"
date: 2012-11-05
forum: Hardware
---

### Post by flowerdealer on 2012-11-05
Hi, I just upgraded my desktop to 12.10. The keyboard and mouse are just not detected. I've tried booting into a usb live image and the same thing too. They keyboard is a K400 logitech keyboard and it worked fine under 12.04. It also works fine under 12.10 in my laptop... Any ideas? I'm really stuck here because this is the only keyboard I have and I don't know hot to proceed to fix the issue without a keyboard itself...

---

### Post by flowerdealer on 2012-11-05
Actually, even a wired mouse and keyboard has this problem, both from my installed version and a live usb image. What a horrible problem.

---

### Post by bjforesthowell on 2012-11-05
You might want to keep an eye on this thread, we all seem to be having the same issue. Mine is doing the same thing, I thought it was the wireless keyboard and mouse, then I went wired and it's the same problem either way.

Is everything working for you at the log on screen?

[http://ubuntuforums.org/showthread.php?p=12337827#post12337827](http://ubuntuforums.org/showthread.php?p=12337827#post12337827)


Here as well...

[http://ubuntuforums.org/showthread.php?t=2059135&page=2](http://ubuntuforums.org/showthread.php?t=2059135&page=2)

---

### Post by flowerdealer on 2012-11-05
Don't know if its related, but I'm also getting weird video glitches on the grub screen... And this happens to the keyboard even when you go into recovery mode...

---

### Post by bjforesthowell on 2012-11-05
I just did a fresh install, and it's not the updates I downloaded. Now, when I log in the screen flickers, it logs me off, and I can see the mouse again while I'm at the log in screen. Whenever I move the mouse the screen flickers more. I'm not dual booting so I don't get the grub screen in order to put myself into the CLI. Do you know how to interrupt the boot so that I can try to fix it from there?

---

### Post by bjforesthowell on 2012-11-06
I've got an NVIDA vido card and this worked for me after working with NikTh (nick-athens30) on launchpad....

During boot you're going to see a purple screen with no Grub options if you're not dual booting. When you see that purple screen hold the [SHIFT] key until grub menu appears and select "Advanced settings".

At this point, you're going to want to select the kernel with the recovery mode options and just hit enter at the next screen.

Once I was in recovery mode I had my input devices and everything was gravy. I was able to run the software update then, while I was in I installed drivers with the directions from this site...

[http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

Now my global menu and launcher aren't coming up, but this shouldn't be a problem to fix now that I've got input devices.

I hope this helps...

---

### Post by bjforesthowell on 2012-11-07
If you've got an Nvidia video card here's how you get your top menu and launcher back after you have access to your input devices...

[http://askubuntu.com/a/202587/104413](http://askubuntu.com/a/202587/104413)

---

### Post by thornside on 2012-11-12
I'm having the same issue.  Installed 12.10 and it doesn't recognize my logitech wireless keyboard or mouse.  They both worked with the live cd.  I opted to have it log me in automatically so I don't know if they would have worked then.

---

### Post by Darkhorse9999 on 2012-12-15
Neither my Roccat Mouse or Logitech keyboard work after updating to Ubuntu 12.10. The are both USB connected. I even tried them in different ports!

Ubuntu gets to the login screen, but obviously, I can't log in as my keyboard doesn't work! It worked fine in Grub.

I have an ATI graphics card so can't really see the connection with that and my mouse and keyboard not working!

Any ideas? Please!

---

### Post by Tiede on 2012-12-16
having the same issue with my wireless keyboard. 
just bought a Vizio CA24-01 all in one, and only the meta, alt, shift and ctrl keys are detected.
at least the touchpad works somewhat *detected as generic mouse, no touchpad settings...
i used that to make my sgs3 android smartphone couple with the system and type using the phone screen as my keyboard. yeah... it s not necessarily the optimal setup, but at least i can type!
that is what i am using to type this.
i am about to file a bug on launchpad for this....

Done.
&#8594; [https://bugs.launchpad.net/linux/+bug/1090956](https://bugs.launchpad.net/linux/+bug/1090956)

---

### Post by YeeP on 2013-01-05
My Logitech wireless (using usb port) is also not working.

According to the mouse, it is version M505.

Of course, the touchpad works just fine, and my usb wired keyboard is also working.

Any updates on ideas on this process?

I checked with a fedora 17 live disc. Same deal.

---

### Post by kevingtonbeare on 2013-06-10
I have upgraded to 13.04 and had the same problem with Logitech wifi keyboard and mouse.  Problem fixed by going into Bios and changing keyboard from wired to USB.  This fixed the mouse also.

Cheers

---

### Post by frank34 on 2014-03-14
be sure with all logitech wireless keyboards that it didn't sercure lock.  To fix make sure if it has an f mode key that it is off and press ctrl-alt-f12.  this usually resets the secure lockout and all is good!  Please pass this along when ever you see logitech wireless keyboard issues.  It's not, necessarily, ubuntu related.

---

