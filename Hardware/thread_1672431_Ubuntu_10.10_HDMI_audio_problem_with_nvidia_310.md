---
title: "Ubuntu 10.10 HDMI audio problem with nvidia 310"
date: 2011-01-20
forum: Hardware
---

### Post by robalrr on 2011-01-20
Hi, I have read many forums and try many solutions but for the moment no one have solved my problem, I have ubuntu 10.10 for 64 bits and a video card NVidia 310m, my laptop is a Dell Vostro 3400.

Can somebody help me with my audio problem, I run the script from alsa and you can see the info of my system here: 

[http://www.alsa-project.org/db/?f=e5117d46e162b93354b28737cc663eb7e8cf72a0]("http://www.alsa-project.org/db/?f=e5117d46e162b93354b28737cc663eb7e8cf72a0")


Thank you for your help

---

### Post by lidex on 2011-01-21
It looks like you are pretty close. Go here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by robalrr on 2011-01-23
Hi I check the link and try the different options, but nothing.

I thought that the probe mask 0x002 (because the option for aplay that works for me is 1,7) will work but after restart I didn't have sound at all.

I think that my problem is I don't know how to say to pulse that my output for HDMI is 1,7. I tried with load-module module-alsa-sink device=hdmi:NVidia in  /etc/pulse/default.pa but I lost the audio at all.

In this moment I am really confused.

---

### Post by lidex on 2011-01-23
> **robalrr said:**
> Hi I check the link and try the different options, but nothing.

I thought that the probe mask 0x002 (because the option for aplay that works for me is 1,7) will work but after restart I didn't have sound at all.

I think that my problem is I don't know how to say to pulse that my output for HDMI is 1,7. I tried with load-module module-alsa-sink device=hdmi:NVidia in  /etc/pulse/default.pa but I lost the audio at all.

In this moment I am really confused.

Maybe you should try this instead:
```
load-module module-alsa-sink device=hw:1,7
```
and forgo the probemask.

---

### Post by robalrr on 2011-01-24
I have HDMI audio, excellent

BTW the option that worked was include in /usr/share/alsa/alsa.conf

```
pcm.hdmi07 {
type plughw
card 1
device 7
}
```

Thanks for your help.

---

### Post by big_troll on 2011-03-03
What kind of HDMI audio do You have?

2+2
5.1
7.1
????

---

### Post by robalrr on 2011-03-03
> **big_troll said:**
> What kind of HDMI audio do You have?

2+2
5.1
7.1
????

I really don't know, I just use the HDMI for connect my laptop to the tv, for watching movies. Sorry

---

