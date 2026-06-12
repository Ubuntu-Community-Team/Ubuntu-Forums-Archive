---
title: "HDD makes strange sound"
date: 2008-05-11
forum: Hardware
---

### Post by art_s on 2008-05-11
Hi all,

Here is my story: I just bought new Asus F3Sg laptop with vista pre-installed. It was okay for a while but then I started noticing strange sound from HDD - it would do some sort of "clicking" twice or four time per minute.

Hdd is ST9250827AS, 232.88 Gb as per gparted info

I thought that's a hdd problem and downloaded seagate tools, ran extensive tests - nothing was there. I also did full surface test - nothing was found.

Then I noticed that when windows is not running (say, while still in boot menu or in bios) this sound is not there. So I though that Windows is the problem and ran Ubuntu LiveCD.

It was all good until I actually installed it. That weird HDD sound apears again. It's even happening when there's no activity in the system.

Is that the sign of drive dying? But why all tests are OK? Why this is not happening every time?

Could that have something to do with power management, say, trying to torn off the disk?

Thanks for all your comments!

---

### Post by EXCiD3 on 2008-05-11
I think this is just normal activity of your hard drive. I have several external hard drives and internal ones that have the same clicking noise. This only happens when the head in the drive is moving and reading/writing data to the drive. When there is very little hard drive activity the sound will go away because the head is not moving. All my drives are still in great condition and have had no problems even with the clicking noise. I dont think you should be worried.

---

### Post by art_s on 2008-05-11
> **EXCiD3 said:**
> This only happens when the head in the drive is moving and reading/writing data to the drive. 

It's different to any sound of read/write activity sounds. In fact, I never heard that "clicking" when hdd was doing something.

It just happens in the idle mode.

---

### Post by Aearenda on 2008-05-11
Could be aggressive head parking by the manufacturer - see [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Interesting that it happens with Windows too.

---

### Post by art_s on 2008-05-11
> **Aearenda said:**
> Could be aggressive head parking by the manufacturer - see [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Interesting that it happens with Windows too.

Thanks for the link - after some reading I installed smartmontools and yes, it appears to be the exact problem.

After each "click" the Load_Cycle_Count increases by one. This is really stupid, because while laptop is on battery, why the hell do I need any bloody parking? 

Anyhow, thanks for this info, I'm looking into that!

---

### Post by zgornel on 2008-05-11
To avoid this, do a :
```
sudo hdparm -B 255 /dev/sda
```. This should disable power management and stop it from parking it's heads. To permanently apply it, edit /etc/hdparm.conf and put apm=255 in the /dev/sda section, assuming that /dev/sda is your hdd.

---

