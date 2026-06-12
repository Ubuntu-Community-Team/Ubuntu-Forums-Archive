---
title: "Gutsy Lenovo t61p (almost) working"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by jakebolewski on 2007-09-23
I recently purchased a t61p from Lenovo and although I had to wait two months to get the damn thing I am glad that I waited.  I played around with Vista but I have but decided that it wasn't worth dual-booting for. I wanted to install Gutsy x64 but had some trouble with video card recognition during boot up (both from the live cd and from the text based install)  My first question is how would I solve this problem.  I know my way around the command line but in order to fix the problem I need at least some visual.  As of yesterday when I completed the text based install Ubuntu would start to boot and then as Ubuntu loaded the screen turned blank never to turn on again.

Discouraged I tried the i386 version of Gutsy which booted and installed relatively flawlessly.  I downloaded and installed the nvidia drivers with Envy and everything seems to be working with the video card.  Some observations I have are (and if anyone could give me answers to fix these problems that would be great)

Gutsy does not recognize the wireless card Intel abgn (model 4 something, sorry for my ignorance)
Sound is not working

Nvidia drivers are working but Compiz seems to be doing some funky things.  The computer should be able to handle compiz no problem based on specs, but every time I try to do something that 3-d intensive such as the cube the computer runs at like 100% and bogs down.  Is this normal?  I thought that the great thing about compiz was that everything is rendered in the gpu so all the fancy effects do not really impact processor performance.  Even resizing windows causes the processor to spike to 100%.

I need to get wireless to work first to install the updates. Here at school they charge you for every byte you download/upload across your wired internet connection.  Wireless is free.

Any help solving /clarifying these problems would be great.  Thanks

-Jake

---

### Post by jakebolewski on 2007-09-23
two things I left out...

If anyone can tell me a way around the video card problems to install the x64 version of Gutsy I would perfer to use the x64 bit version over the i386 version of ubuntu ( I paid almost $2000 for this laptop, I would like it to run at its maximum potential)

-and-

In settings monitor the first time I installed i386 Gutsy the computer recognized two "cpu's" or cores and displayed both "cpu" in the CPU history.  When I reinstalled trying to get the Nvidia driver to work, the settings Monitor failed to recognize two cores and now just displays one cpu.

---

### Post by KeighleHawk on 2007-09-25
No help from me, just thought I'd ride your coat tails to a solution.  I pretty much got my butt kicked by both Fiesty and Gutsy on my T61p.  Mine has the WUXGA screen so I don't know if that is an added complication.  I tried several things so the results below may be a bit out of order until I can give it another go and be more systematic.  Fiesty installed so well on both a Dell M60 and Dell M90 I was not expecting trouble from my T61.

Problem 1:  Video.  I had to install using "Safe Graphics" mode.  Sucked, but okay.  Sucked a little extra with Fiesty because the dialog boxes are too big and not adjustable so I could never actually see the buttons at the bottom of the dialog.

Problem 2:  Nvidia drivers.  I had a couple different results here and don't recall at the moment which effort produced which result.  At one point, They seemed to install fine, but the screen refused to display the resolution it claimed it did.  Kinda like it was still in "safe" mode.  Other times it borked X entirely and so refused to boot.

Problem 3:  Wireless.  At first on Gutsy, it seemed to find the wireless card just fine.  Fiesty did not.  However, on Gutsy, when I installed the NVidia drivers, I lost wireless.  That made no sense at all.  At another time, I was getting a lot of complaints from wpa-supplicant while trying to shutdown.

Problem 4:  Hard Drive.  My 160GB hard drive was getting recognized as only 75GB.  hmmm....

---

### Post by jakebolewski on 2007-09-25
Are you using x64 or i386 version of Gutsy?

I reinstalled the i386 version and this time I did not even touch the restricted Nvidia driver.  I managed to get the wireless card working just enough to install the updates (like 500 of them) for gutsy.  After updating the computer things are starting to come together.  Sound works when you follow the guide to set it up on the thinkwiki Gutsy site.  Wireless is working much better.  Two cores are recognized and overall performance seems to be much better.

My advice to you would be to not install the Nvidia driver as it is more trouble than it is worth.  Go with the standard unaccelerated driver in Gutsy which seems to be a lot more stable and ties up less system resources.

--Still a few problems--
Only one usb port on the left hand side of the computer is working.
Still have problems with suspend/resume + hibernate

Hopefully things will start coming together in the next couple of weeks building up to the stable release of Gutsy.

-Jake

---

### Post by tienhn on 2007-10-06
I have t61p and have been using 7.04 until a few days ago I updated to Gutsy Beta.
1/ Audio is now working. On 7.04, I had to download and build a newer release of ALSA.
2/ All USB port works on my laptop even when I was on 7.04. Even though I read some complains that the right side USB does not work.
3/ The Media card slot works for me.
4/ I still have not found a good way to fix the Hibernation and Suspense mode. It never come back ofter Suspense or Hibernation.

I found this site is quite useful:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61)

Cheers,

---

### Post by TihSon on 2007-11-04
I have read your stories and I wish I could be as optimistic. Any advise would be appreciated. I also have a T61p, but instead of a poorly working system, I have a brick. I have been at it four days now, and all I have managed to do is get the text based installer to format the drives. Everything else I have found from Google, Ubuntu Forums, Thinkwiki, etc, etc, etc, has not worked. My paranoid side makes me think Lenovo and nVidia want to send a message to us Linux users to stay away.

Currently when I boot I get the Thinkvantage splash, a Kubuntu splash, then a cursor in the top left corner. At this point virtually nothing works.

I think the problem stems from the nVidia Quadro 570m, but I can't even get into a terminal to access the xord.conf.

I have been trying to switch to Kubuntu for almost 2 years, and this one was supposed to be it, so any help would be very much appreciated.

---

### Post by minotaurjim on 2007-11-05
I've had no problems installing on my T61p

Just run the text based install.  After it completely installs and it's time for the reboot press "esc" to get to the grub boot loader when it prompts you (you only have 3 or so seconds to hit it.

Once in there pick the "recovery" option.  That will boot to a command prompt.

From there use your text editor of choice.  I used vi.

edit the xorg.conf and where it says "nv" in the video card place change it to "vesa".  save and reboot normally.

the gui will start and from there you can install the nvidia restricted drivers or keep the regular vesa drivers.



***

I myself have a problem with getting the wireless card to work.  but somone mentioned that the nvidia drivers may be the culprit.  I guess I'll go back to the vesa ones until it gets a workaround or resolved.

---

### Post by MountainX on 2008-02-23
I have Gutsy running on my T61p. Start with this link:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

### Post by MountainX on 2008-02-23
> **minotaurjim said:**
> 

I myself have a problem with getting the wireless card to work.  but somone mentioned that the nvidia drivers may be the culprit.  I guess I'll go back to the vesa ones until it gets a workaround or resolved.

I got my wireless working with the nv driver. See this link:

[http://ubuntuforums.org/showthread.php?t=699442](http://ubuntuforums.org/showthread.php?t=699442)

---

