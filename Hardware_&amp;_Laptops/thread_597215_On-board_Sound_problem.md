---
title: "On-board Sound problem"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Liberi on 2007-10-30
I have a Gateway MZ3707 Laptop (or that's what it says on the bottom of the silly thing) that I just swaped over to Ubuntu 7.10. Other then the mild chaos of getting everything needed so it can run things well, I seem to have one other problem: My sound isn't working. THis only half-bothers me, but I'd lke to know if I can get it back to working order.

I am new at this, but I do know how to get into the terminal, if that counts for anything.

---

### Post by dabl on 2007-10-30
Here's pretty good guidance on troubleshooting sound issues:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

:)

---

### Post by Liberi on 2007-10-30
Thanks.

EDIT: kay, this is really odd....Detects the sound card(s!), and they are not muted. So...what gives?

---

### Post by Liberi on 2007-10-30
Okay...this is really odd. Follow guide, sound card detected, allowed, and not muted. But no sound. Any help on this?

---

### Post by dabl on 2007-10-30
You may just need to twiddle the "mixer" settings.  Right-click the speaker icon, choose "open mixer" or "show mixer" or whatever it says, then get to the settings and see if you can work on the output channel(s).  Make sure all the channels have the volume set reasonably, no muted channels, etc. :)

---

### Post by Liberi on 2007-10-30
*messes with "Volume Control" (that's what it gives me), plays test song*

Err....still nothing. Test Song is on Youtube...and I have no other applications running. Master Volume and PCM Volume cranked to 11, Captures all at null. This is odd, really odd.

---

### Post by dabl on 2007-10-30
I'm not sure youtube is the best test source for sound -- I think you need working codecs, which you may not have yet.

Do you hear the "drums of Ubuntu" when you log in? Or is it totally silent at all times?  Do you know what your sound chip is -- you can do ```
lspci
``` in a console window and it should show up.

---

### Post by Liberi on 2007-10-30
No drums. Drums was the start-up sounds? Wow.

Direct copy-pasta of read-out (audio).

> 00.14.2 Audio Device: ATI Technologies Inc. SB450 HDA Audio (rev 01)

I think I am missing a codec. Not sure, though. (am new to this)

---

### Post by dabl on 2007-10-30
Unfortunately, it would appear you are not alone:

[http://ubuntuforums.org/showthread.php?p=3466066&highlight=sb450#post3466066](http://ubuntuforums.org/showthread.php?p=3466066&highlight=sb450#post3466066)

That was the first hit I got on the "Comprehensive Sound Guide" thread.  If you go back to that thread, there is a "Search This Thread" window, and if you put "sb450" in it, there were a number of hits, and I only looked at one.  You might want to browse through them and see if anyone has come up with a reliable solution (other than installing Feisty).   :-({|=

---

### Post by Liberi on 2007-10-30
Alright, I'll look through that. Thanks for the help!

---

### Post by dabl on 2007-10-30
I found a possible fix, that worked for problems with that chip in Feisty.  In a console window:

```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
```


I found that here:

[http://ubuntuforums.org/showthread.php?t=415821&highlight=sb450&page=2](http://ubuntuforums.org/showthread.php?t=415821&highlight=sb450&page=2)


No guarantees -- it's kind of old third-hand information.  But I don't think you'll make it any worse!  :lolflag:

---

### Post by Liberi on 2007-10-30
I think that would work....if the modual wasn't in use.

[quote=error]ERROR: Module snd_hda_intel is in use[/quote]

DX

EDIT: Nevermind....found workaround for error in said thread. Thank you!

---

### Post by dabl on 2007-10-30
Yay!  Now quick, write down how you did that!   :lolflag:

---

### Post by Liberi on 2007-10-30
err....it's not working. At all. Heck, it spits out a "no codecs initialized" or something like that after the second command.

Yes, I did check out the thread. Yes, I did try the slightly different version that was posted in there. No, it did not give me something different. #-o

EDIT: GOing to try something....odd 

Edit Edit:Err....just noticed, that's for 7.04, and for Toshiba, not Gateway.

---

### Post by dabl on 2007-10-30
#-o

is right!

OK, well I guess you might as well try the script on this page:

[http://ubuntuforums.org/showthread.php?t=415821&page=10](http://ubuntuforums.org/showthread.php?t=415821&page=10)

You'll have to open gedit as "Super User" by running ```
gksu gedit
``` then paste in the script and save the file with the name ```
alsa_setup.sh
``` in your user folder.

Then you'll run the commands shown below the script, and who knows? -- maybe have sound!  :)

---

### Post by Liberi on 2007-10-30
um....

[quote=after running script]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/quote]

o.O

---

### Post by dabl on 2007-10-30
That's not a desirable result!  ](*,)

Here's the bug on Launchpad -- kind of a sad little story, if you read down to the bottom:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136308)

:(

---

### Post by Liberi on 2007-10-30
Found a thread on wifi/audio problems on the Gateway MT 3705 laptop after looking though launchpad via. that link. I have a MT 3707, so I think it will still work if I follow the audio instructions of that one.

EDIT: Grah....this thread has a suggestion, but I don't want to... [http://ubuntuforums.org/showthread.php?t=352553&page=7](http://ubuntuforums.org/showthread.php?t=352553&page=7) last post has a way, but I need to go through all that fun again of getting a live CD for Ubuntu...

---

