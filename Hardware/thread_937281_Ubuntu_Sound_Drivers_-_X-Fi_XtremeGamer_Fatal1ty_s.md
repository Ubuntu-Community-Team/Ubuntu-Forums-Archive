---
title: "Ubuntu Sound Drivers - X-Fi XtremeGamer Fatal1ty series"
date: 2008-10-03
forum: Hardware
---

### Post by gtno on 2008-10-03
Hello,

I have two sound cards in my system.  One being onboard sound drivers, which are installed and working fine, and I also have an X-Fi XtremeGamer Fatal1ty Pro card that I would like to be installed as well.  Is there away to make these both run together, because I like to use anything requiring a microphone through my headset which is connected to my onboard sound and I used my X-Fi card with my surround sound.  I know X-Fi has problems with linux, but I just wanted to know if this is possible.

---

### Post by markbuntu on 2008-10-03
If you are having problems getting your Creative X-FI card to work you need to use OSS4 or recompile your kernel with a patched X-Fi driver: 

To get OSS4:

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can seriously break your system,  do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

Be sure to read these threads and ask some questions before you take these somewhat drastic steps.

If you recompile the kernel, you can use both your cards together easily with PulseAudio, I am not so sure with OSS4, I have not tried it yet.

---

