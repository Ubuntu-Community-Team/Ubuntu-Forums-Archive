---
title: "Dell XPS 1330 latop - resume from suspend doesn't work"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by nikdo on 2007-11-10
Hello fellow ubuntu users.

Just like you, I love Ubuntu Gutsy. And I love it even more on my brand new Dell XPS 1330. Man, that machine rocks and with Gutsy on it, it's flying! When people see it, it makes many of them jealous they're running Vista!

One thing that spoils my fun and productivity is the suspend. Ubuntu suspends all right, but the resume doesn't work. I will usually see yellow "linu" written, with a blinking cursor in front. Sometimes that's all I get. Other times I will see lines of text written...usually it stops on errors trying to get the SATA HDD back online. Bottom line, it never ever resumes (this is not hibernate, just suspend). I know I'm not being specific enough; however I am not exactly sure where to go to give a more full report as to what is written to the screen or done when I am resuming. I assume it must be in some log file...I just don't know exactly where (any ideas?).

I have tried to go back to the regular nvidia drivers ubuntu first installed with and disable compiz to see if that fixed things, but still the same problem (the driver it first installs with automatically is "nVidia Corporation G80 [GeForce 8400M GS]" - from xorg.conf)

My setup is Dell XPS 1330 with dual intel 1.8 Ghz CPU, 3 Gig RAM, LED screen, 150Gig SATA HDD, nvidia 8400 video card, Bluetooth, the regular intel Wifi, fingerprint reader.

So far everything (except fingerprint reader and webcam - haven't had the chance to try those out yet) seems to work beautifuly.

Any help would be greatly appreciated. I have searched these forums and the net and had little success finding info. A lot of people succeeded in resuming from suspend with the same configuration I have, others haven't - but the solutions I have seen are few and a bit bizarre and inconsistent.

Thank you so much for your help!

---

### Post by thingy on 2007-11-10
See if the following URL is helpful:

[http://blog.higherthings.org/borghardt/article/3077.html](http://blog.higherthings.org/borghardt/article/3077.html)

Specifically the Suspend & Hibernation section

---

### Post by nikdo on 2007-11-10
Thank you for the reply. I have looked at that thread, but unfortunately the article seems to mention the issue being compiz-fusion. I have disabled it by going to Appearance Preferences - Visual Effects and putting effects to none. I have also reverted to the original nvidia driver gutsy installs. Then I tried to resume fro ma suspend and got a black screen.

I would love to hear from people who got the same problem and fixed it, or people that have the suspend working for them. Most of us using the XPS 1330 have the same hardware - so how come there's so many different stories as to suspend working or not working?

Thanks everyone for helping out

---

### Post by thingy on 2007-11-11
Can you confirm that you made the following changes:

```

[SIZE=2]sudo gedit 			/etc/default/acpi-support[/SIZE]
[SIZE=2]…[/SIZE]
             [SIZE=2]# Should we attempt to warm-boot the video hardware  on resume?POST_VIDEO=false 
[/SIZE]
             [SIZE=2]# Should we save and restore state using VESA BIOS Extensions?SAVE_VBE_STATE=false
  …[/SIZE]

```

The article is saying that for your machine, after resuming from suspend, the video hardware should not be warm booted and the VBE state should not be restored.

Compiz-fusion might be one cause of the machine's failure to resume but there can be others. To get some background on why suspend is not "plug and play", look at this:

[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)


What you need to find out is:

- Whether your machine resumes properly from a suspend to ram but the display hasn't been resumed properly. This is the best scenario since the fix is something simple like the above setting change in the acpi-support script or a kernel boot param

To test if the machine resumes properly, make sure its connected to the network and you know its ip and then on another machine continuously ping your laptop. You should see the ping replies drop when its suspended and come back again when you resume.

- If the machine is not resuming properly (i.e. machine has hanged) then its a long winded process of de terming which hardware device is causing the resume to fail and then if that device is compiled into the kernel as a module, to unload and reload the module when suspending/resuming respectively. (this is a dirty way of doing this...until someone fixes the driver for the device)


See the Compatibility + Using TuxOnIce sections at this url for more background:

[http://www.tuxonice.net/FAQ](http://www.tuxonice.net/FAQ)


jin

---

### Post by erginemr on 2007-12-26
Please follow this bug report and try removing / disabling problematic "processor" kernel module as suggested therein:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137477](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137477)

Also have a look at the following pages:
[http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20)

which focus on enabling / disabling ACPI parameters via Grub.

Finally, the following page refers to problems in DELL Laptop XPS 1330 and their solutions:
[http://blog.higherthings.org/borghardt/article/3077.html](http://blog.higherthings.org/borghardt/article/3077.html)

Please check out the section for "Suspend & Hibernation" there.

---

### Post by jespdj on 2007-12-26
Resume from suspend works fine on my M1330. The only small problem is that after resuming, the sound volume is on maximum.

The M1330 comes in different hardware configurations, so it might work with one hardware config and not with another. See my signature below for my configuration.

---

