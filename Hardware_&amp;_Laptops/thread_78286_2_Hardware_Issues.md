---
title: "2 Hardware Issues"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by rmco2003 on 2005-10-18
I've just finished installing my dual-booted Ubuntu OS and I have 2 seperate problems.

The first problem is with my sound card, I've seen that this issue has been unresolved in the new version of Ubuntu so I guess I'll bring it to attention, since I haven't seen it in the Sound help forum. My sound card is a Sound Blaster Live 24-bit edition, Linux recognizes it as Audigy LS or something along those lines, sound does not work for me, and I've tried changing options in the media system selector tool but it fails to use ALSA and OSS so I reverted it to default settings. I'd appreciate some help with this, I don't want to use my internal sound card, which Linux has apparently chosen to use instead of my Sound Blaster card.

The second problem is my internet access, it recognizes my Speedtouch 330 modem now, and I see that both the USB and ADSL lights are green, so the only thing I need to know is how can I get it to login so I can browse on ubuntu?

Hope I get some help this time around.

---

### Post by rmco2003 on 2005-10-19
Will someone at least try to solve one of my problems? I've been ignored constantly on these forums, it's ridiculous.

---

### Post by John.Michael.Kane on 2005-10-19
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28sound%29](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28sound%29)
[https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29](https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29)
[https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29](https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29)
[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+blaster](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+blaster)
[http://www.ubuntuforums.org/showthread.php?t=19307&highlight=sound+blaster](http://www.ubuntuforums.org/showthread.php?t=19307&highlight=sound+blaster)
[http://www.ubuntuforums.org/showthread.php?t=31829&highlight=sound+blaster](http://www.ubuntuforums.org/showthread.php?t=31829&highlight=sound+blaster)

As for your modem system>administration>networking> activate your modem or networking card ect 
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29)
[https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28dsl%29](https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28dsl%29)

---

### Post by rmco2003 on 2005-10-20
Thanks for the help, I'll see if it works out ok.

---

### Post by rmco2003 on 2005-10-20
I've tried the adsl modem guide, and that's been a complete failure, as it was scanning my ethernet ports, and I have a USB ADSL modem, so there's no way that's gonna work. And I saw in one of the sound guides I had to download packages, so unless the internet problem is sorted out, I can't fix my sound. Any ideas?

---

### Post by Ptero-4 on 2005-10-20
You can download the sound stuff from Windoze. To do that go to [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) and navigate through the links (which correspond to "main", "universe", etc) until you find the right packages (to do that use apt-get to iniciate the installation of your sound card sw but instead of installing it write down the dependencies and then manually download them from windoze). After finding and d/l'ing the stuff, from within ubuntu copy the debs to /var/cache/apt/archives and install the sound sw. This time apt uses the packagues that are in it's cache.

---

### Post by rmco2003 on 2005-10-20
I'd like to get my internet working most of all, are there any guides to get my USB Copperjet 330 modem working?

---

### Post by John.Michael.Kane on 2005-10-20
rmco2003 These may help with your modem...

[http://www.xs4all.nl/~pschram/english.html](http://www.xs4all.nl/~pschram/english.html)
[http://tldp.org/HOWTO/DSL-HOWTO/speedtouchusb.html](http://tldp.org/HOWTO/DSL-HOWTO/speedtouchusb.html)
[http://www.linux.org/docs/ldp/howto/DSL-HOWTO/](http://www.linux.org/docs/ldp/howto/DSL-HOWTO/)
[http://christophe.delord.free.fr/en/adsl/](http://christophe.delord.free.fr/en/adsl/)

---

### Post by rmco2003 on 2005-10-21
The first link looks like it could work but when I use ./configure it said that I don't have gcc, cc, cc or cl installed, so I installed gcc and now it says that gcc can't make executable files, this is just getting worse and worse, what can I do now?

---

### Post by rmco2003 on 2005-10-24
Help anyone?

---

### Post by rmco2003 on 2005-10-26
Well since no-one cares about helping me I might as well uninstall ubuntu for a second time and hope that in the next revision, they might actually consider that some of us would like to get usb ADSL modems working without using the terminal, and that some of us actually like sound on operating systems.

---

### Post by John.Michael.Kane on 2005-10-26
I tried to help with the infoi posted. I'm sorry however that it was of no help.

---

