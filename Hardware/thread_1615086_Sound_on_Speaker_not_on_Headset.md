---
title: "Sound on Speaker not on Headset"
date: 2010-11-06
forum: Hardware
---

### Post by jesuisbenjamin on 2010-11-06
Hello there,

I installed 10.10 on a Packard Bell Easynote. It's working like a charm except for one thing: sound does not come from the headset output whilst it does from the speakers. What can i do to fix this?
Preliminary information:
[LIST]
[*]The headset are working fine
[*]Headset output used to work fine under Vista
[*]Soundcard: ATI Technonogies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
[/LIST]

Thanks!
Benjamin

---

### Post by jesuisbenjamin on 2010-11-18
Hi people! 

Can you please help me trouble-shoot this? :D Thanks

(this community rocks by the way)

---

### Post by jesuisbenjamin on 2010-11-22
Bump!

Anyone there to help? Please? :)

---

### Post by jesuisbenjamin on 2010-11-25
[B]Bump again:
[/B]
Hello there,

I installed 10.10 on a Packard Bell Easynote. It's working like a charm except for one thing: sound does not come from the headset output whilst it does from the speakers. What can i do to fix this?
Preliminary information:

    * The headset are working fine
    * Headset output used to work fine under Vista
    * Soundcard: ATI Technonogies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


Thanks!
Benjamin

---

### Post by dandnsmith on 2010-11-25
The really interesting thing is that it used to work under Vista (did you get sound from both, or just the headphones when they were plugged in?)

I haven't tangled with sound problems recently, but suggest it could be in options for the alsa manager, or whatever gets used in Ub 10.10

Another possibility is the detection of the actual headphone insertion - what type of connector is used, and what is it plugged in to (eg sound card, motherboard, front panel ...)

---

### Post by jesuisbenjamin on 2010-11-25
> **dandnsmith said:**
> did you get sound from both, or just the headphones when they were plugged in?

I am not sure about that. I believe headset was singled out when plugged in.

> **dandnsmith said:**
> 
whatever gets used in Ub 10.10
That would be Pulse Audio

> **dandnsmith said:**
> 
Another possibility is the detection of the actual headphone insertion - what type of connector is used, and what is it plugged in to (eg sound card, motherboard, front panel ...
Well it's a laptop, the connection is with a jack on the front side, so i imagine it's connected directly to the integrated sound-card (which it is mostly what it is in laptops right?).

Also i just found this bug [exists since a while in Launchpad already]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215586").
:(

---

### Post by dandnsmith on 2010-11-25
Yes, they're mostly direct connection.

That link sounds rather depressing - could well be your problem (mine too, when I get to testing that feature eventually)

---

### Post by anurak_d on 2010-11-28
Me, too.
Everything on Win7 are usually (I mean both speaker&headphone)
Anyone can help? I try to do like an old posted but it doesn't work!
hope someone have the same problem and clear it, who knowledgeable.

---

### Post by jesuisbenjamin on 2010-12-11
Hello there,

Is there anyone that can help fix this problem? Is there any way to know whether this problem will be fixed in the 11.04?

I'd like to listen to my music on speakers, so help would be _really_ appreciated.

Thanks,

Benjamin

---

### Post by IcarusR on 2010-12-11
Software modems can have an adverse effect on sound. If you do not use modem try blacklisting it's module. Add module to /etc/modprobe.d/blacklist.conf 

Also if you use snd-intel-hda module then maybe adding 'model=your model' to /etc/modprobe.d/alsa-base.conf as per these two threads will help.

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by jesuisbenjamin on 2010-12-11
> **IcarusR said:**
> Software modems can have an adverse effect on sound. If you do not use modem try blacklisting it's module. Add module to /etc/modprobe.d/blacklist.conf 

Also if you use snd-intel-hda module then maybe adding 'model=your model' to /etc/modprobe.d/alsa-base.conf as per these two threads will help.

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Hi!
thanks for your response. I don't understand what you mean by "software modems" and what "module" i should add to the blacklist.conf.

Also the computer in question is a Packard Bell laptop, of which the sound-card is: ATI Technonogies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
I imagine the Intel HDA solution does not apply(?).

Thanks for clarifying.

Benjamin

---

