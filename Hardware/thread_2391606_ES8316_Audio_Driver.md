---
title: "ES8316 Audio Driver"
date: 2018-05-11
forum: Hardware
---

### Post by shuncey on 2018-05-11
Hey Guys,
So i just installed lubuntu 18.04 On my Axon Cloudbook (A strange brand from thailand) which came with windows 10 but my school prefers linux so you know i installed lubuntu since it only has 2GB of RAM and a Z8350 Quad 1.44Ghz ok so lemme get this straight so i followed this tutorial of installing the drivers for audio(ES8316) -> [https://www.koyst.com/manu/114.html](https://www.koyst.com/manu/114.html) and it gives me error all the time could you help me i did all the steps. 
so here's lspci

00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)

and here is the result of [COLOR=#000000]cat /proc/asound/cards

[/COLOR]0 [Audio          ]: HdmiLpeAudio - Intel HDMI/DP LPE Audio
                      Intel HDMI/DP LPE Audio
 1 [bytchtes8316   ]: bytcht-es8316 - bytcht-es8316
                      LIVEFAN-LIVEFAN--LIVEFAN
 any help will be aprpreciated

---

### Post by oldos2er on 2018-05-11
Moved here from Resolution Centre, which "is the place to contact a forum admin concerning problems with your  forum account, to appeal moderator action, to request a thread be moved  from the jail, or to file a complaint about forum harrassment or abuse."

---

### Post by shuncey on 2018-05-11
i actually google translated it but when i compile it here's the output
/home/shuncey/es8316/sound/soc/codecs/Makefile
make: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
make[1]: *** No rule to make target '/home/shuncey/es8316/sound/soc/codecs/ac97.o', needed by '/home/shuncey/es8316/sound/soc/codecs/snd-soc-ac97.o'.  Stop.
Makefile:1552: recipe for target '_module_/home/shuncey/es8316/sound/soc/codecs' failed
make: *** [_module_/home/shuncey/es8316/sound/soc/codecs] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
mv: cannot stat '*.ko': No such file or directory
/home/shuncey/es8316/sound/soc/intel/atom/sst/Makefile
make: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
make[1]: *** No rule to make target '/home/shuncey/es8316/sound/soc/intel/atom/sst/es8316.o', needed by '/home/shuncey/es8316/sound/soc/intel/atom/sst/snd-soc-es8316.o'.  Stop.
Makefile:1552: recipe for target '_module_/home/shuncey/es8316/sound/soc/intel/atom/sst' failed
make: *** [_module_/home/shuncey/es8316/sound/soc/intel/atom/sst] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
mv: cannot stat '*.ko': No such file or directory
/home/shuncey/es8316/sound/soc/intel/boards/Makefile
make: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
make[1]: *** No rule to make target '/home/shuncey/es8316/sound/soc/intel/boards/haswell.o', needed by '/home/shuncey/es8316/sound/soc/intel/boards/snd-soc-sst-haswell.o'.  Stop.
Makefile:1552: recipe for target '_module_/home/shuncey/es8316/sound/soc/intel/boards' failed
make: *** [_module_/home/shuncey/es8316/sound/soc/intel/boards] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
mv: cannot stat '*.ko': No such file or directory

---

### Post by nicofossa on 2018-05-15
I succesfully compiled the drivers: just put the two line in the correct Makefile as states in the second code snippet. Google Translate should be enough to understand it.
Then launch the last script  to compile the modules.
See my answer [here]("https://askubuntu.com/questions/1034619/problem-with-audio-device-es8316-and-ubuntu-18-04"), it may help!

---

### Post by shuncey on 2018-05-15
This is kind of a stupid answer but, even if I Google Translate it i dont understand a thing do i create a makefile in sound/soc/intel/atom/sst and write this there
# sound/soc/codecs/Makefile
snd-soc-es8316-objs := es8316.o
obj-m    += snd-soc-es8316.o

# sound/soc/intel/boards/Makefile
snd-soc-sst-byt-cht-es8316-objs := bytcht_es8316.o
obj-m += snd-soc-sst-byt-cht-es8316.o

# sound/soc/intel/atom/sst/Makefile
snd-intel-sst-acpi-objs += sst_acpi.o
obj-m += snd-intel-sst-acpi.o

and then make a .sh file containing this 

# ubuntu
C_FLAGS="-C /usr/src/linux-headers-`uname -r`"
# opensuse
# C_FLAGS="-C /usr/src/linux-`uname -r`"
c_dir=`pwd`
for mf in `find $c_dir -type f -name "Makefile"`
do
    echo $mf
    cd `dirname $mf`
    make $C_FLAGS M=`pwd` modules
    mv *.ko $c_dir
    cd $c_dir
done

???
Thanks

---

### Post by nicofossa on 2018-05-15
Ok so, here it is the procedure step by step.
Open a terminal, create a new folder, enter in it.
Then:


```
nano download.sh

```Paste the following code:


```
# &#21407;&#22987;&#20986;&#22788;#p_url='https://raw.githubusercontent.com/yangxiaohua1977/sound/master'
# &#23558;&#35201;&#21512;&#24182;&#21040;kernel&#20013;&#30340;&#20195;&#30721;&#65292;&#20351;&#29992;&#36825;&#20010;&#20179;&#24211;&#20013;&#30340;&#20195;&#30721;
p_url="https://raw.githubusercontent.com/dsd/linux/es8316"
files="
sound/soc/codecs/es8316.c
sound/soc/codecs/es8316.h
sound/soc/codecs/Makefile
sound/soc/codecs/Kconfig
sound/soc/intel/Kconfig
sound/soc/intel/boards/Makefile
sound/soc/intel/boards/cht_bsw_es8316.c
sound/soc/intel/boards/bytcht_es8316.c
sound/soc/intel/sst/atom/sst_acpi.c
sound/soc/intel/atom/sst/sst_acpi.c
sound/soc/intel/atom/sst-atom-controls.h
sound/soc/intel/common/sst-acpi.h
sound/soc/intel/common/sst-dsp.h
sound/soc/intel/atom/sst-mfld-platform.h
sound/soc/intel/atom/sst/sst.h
sound/soc/intel/atom/sst-mfld-dsp.h
"
for f in $files
do
    echo $f
    mkdir -p `dirname $f`
    wget $p_url/$f 
    mv `basename $f` $f 
done

```then:


```
chmod +x download.sh
./download.sh

```and wait until the scripts download the needed files.


Then:
```
rm sound/soc/codecs/Makefile
rm sound/soc/intel/boards/Makefile
rm sound/soc/intel/atom/sst/Makefile

```Then:


```
nano sound/soc/codecs/Makefile

```and paste:


```
snd-soc-es8316-objs := es8316.o
obj-m    += snd-soc-es8316.o

```Then:


```
nano sound/soc/intel/boards/Makefile

```and paste:


```
snd-soc-sst-byt-cht-es8316-objs := bytcht_es8316.o
obj-m += snd-soc-sst-byt-cht-es8316.o

```Then:


```
nano sound/soc/intel/atom/sst/Makefile

```and paste:


```
snd-intel-sst-acpi-objs += sst_acpi.o
obj-m += snd-intel-sst-acpi.o

```Then:


```
nano compile.sh

```Paste:
```
# ubuntuC_FLAGS="-C /usr/src/linux-headers-`uname -r`"
# opensuse
# C_FLAGS="-C /usr/src/linux-`uname -r`"
c_dir=`pwd`
for mf in `find $c_dir -type f -name "Makefile"`
do
    echo $mf
    cd `dirname $mf`
    make $C_FLAGS M=`pwd` modules
    mv *.ko $c_dir
    cd $c_dir 
done

```Then:


```
chmod +x compile.sh
./compile.sh

```

---

### Post by shuncey on 2018-05-15
I'm litteraly crying it works!
Thank You So Much Man!

Well i failed after minutes of waiting this came out of nowhere
```
/home/shuncey/sound/sound/soc/codecs/Makefile
make: *** No rule to make target 'modules'.  Stop.
mv: cannot stat '*.ko': No such file or directory
/home/shuncey/sound/sound/soc/intel/atom/sst/Makefile
make: *** No rule to make target 'modules'.  Stop.
mv: cannot stat '*.ko': No such file or directory
/home/shuncey/sound/sound/soc/intel/boards/Makefile
make: *** No rule to make target 'modules'.  Stop.
mv: cannot stat '*.ko': No such file or directory
```

Hey still need help. Thanks Sorry new to ubuntu

Hey Guys Problem is solved. So i made a script that you guys can try if you have the es8316 on linux.
[https://drive.google.com/file/d/1bIJTzBdMDejj8-6Er8EecjYSDcvULbPx/view?usp=sharing](https://drive.google.com/file/d/1bIJTzBdMDejj8-6Er8EecjYSDcvULbPx/view?usp=sharing)
and just execute it and there audio is working.

---

### Post by guillaume-thomsen on 2018-05-16
Hi !

I am experiencing the same issue with a Yepo 737S, followed the same instructions as shuncey, and received de same error. I'm on this french forum : [https://forum.ubuntu-fr.org/viewtopic.php?id=2026142](https://forum.ubuntu-fr.org/viewtopic.php?id=2026142)

I'm sure we'll find the answer, the community is strong !

---

### Post by shuncey on 2018-05-16
try this out [https://drive.google.com/file/d/1bIJTzBdMDejj8-6Er8EecjYSDcvULbPx/view?usp=sharing](https://drive.google.com/file/d/1bIJTzBdMDejj8-6Er8EecjYSDcvULbPx/view?usp=sharing)

Try the script I made it will probably work with headphones even speaker

---

### Post by guillaume-thomsen on 2018-05-16
Wow, great work !

I ran your script, and it did help : the sound now comes out of the headphones, but still not from the speakers. I'm sure not much is missing to finish the job, but being quite a begginer, I don't know what my next step should be. Alsamixer tells me speaker is shut. There must be an easy way to turn it on ?

Anyway, thanks.

---

### Post by shuncey on 2018-05-16
I'm glad it helped.
Still finding out why speakers doesn't work, I'm sure people are still doing anything they can to make the speaker work.
But still it works.
And Thanks.

---

### Post by guillaume-thomsen on 2018-05-16
Is your sound card, like mine, bytcr-rt5651?

If yes, there seems to have a conflict with the HDMI port (wrongly treated as sound card). Sorry, it's french: [https://forum.ubuntu-fr.org/viewtopic.php?pid=21874250#p21874250](https://forum.ubuntu-fr.org/viewtopic.php?pid=21874250#p21874250)

I tried what's written in there, no success so far. I'll let you know if I find a solution that works for me.

---

### Post by shuncey on 2018-05-16
As you look closely in my script, I have already blacklisted HDMI Audio(echo "blacklist snd_hdmi_lpe_audio" > /etc/modprobe.d/blacklist_hdmi.conf).
And yes i have the rt5651 and also the es8316 Audio Codec. I already have the folder called bytcr-rt5651 in   /usr/share/alsa/ucm/ still no signs of audio in speaker and i also tried updating alsa-driver still doesn't work though but im actually trying my best to do so  any way how do i contact you? You have facebook or something? I'll just update you when audio is working. and which distro are you using?

---

### Post by shuncey on 2018-08-31
Even after months of research, still can't get the speakers to work.

---

### Post by nicolettacau on 2018-09-04
Hi everyone,
I have a Mediacom Flexbook 13.3 and I'm trying to make sound work too.
I executed all the steps described by nicofossa but it didn't work.
Then I ran shuncey's script, but it didn't work either, there's no sound even with headphones.
This is my output from **dmesg | grep 8316**:
```
[   38.076261] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.076275] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.160378] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.160390] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.161049] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.161064] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.612379] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.612522] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
```
Can anybody help me solve this problem?

---

### Post by gcurtsinger on 2018-09-13
I had no sound until I installed pulse audio control. I think it should come by default on Linux systems. Had the same problem with Mint. No problems now.

---

### Post by shuncey on 2018-09-14
> **nicolettacau said:**
> Hi everyone,
I have a Mediacom Flexbook 13.3 and I'm trying to make sound work too.
I executed all the steps described by nicofossa but it didn't work.
Then I ran shuncey's script, but it didn't work either, there's no sound even with headphones.
This is my output from **dmesg | grep 8316**:
```
[   38.076261] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.076275] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.160378] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.160390] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.161049] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.161064] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
[   38.612379] bytcht_es8316 bytcht_es8316: ASoC: CODEC DAI ES8316 HiFi not registered
[   38.612522] bytcht_es8316 bytcht_es8316: snd_soc_register_card failed -517
```
Can anybody help me solve this problem?

Have you tried running my script?
After exececuting my script do "sudo apt install alsa-base && sudo alsa reload"

---

### Post by shuncey on 2018-09-14
If you don't know how i have a tutorial on YouTube
[https://youtu.be/DDSyeEMHKvM]("https://youtu.be/DDSyeEMHKvM")

---

### Post by vihtinsky on 2018-10-21
> **shuncey said:**
> Even after months of research, still can't get the speakers to work.
Got speakers to work by replace sound/soc/codecs/es8316.c with this - [https://github.com/kernins/linux-chwhi12/blob/master/sound/soc/codecs/es8316.c](https://github.com/kernins/linux-chwhi12/blob/master/sound/soc/codecs/es8316.c)
But now both speakers and headphones works at same time.

---

### Post by vihtinsky on 2018-10-22
After trying this modified driver that writes to the gpio. Found that driver turn off/on speakers, but to the first change of sound volume or other switch.
So I get the gpio number from /sys/kernel/debug/gpio with this modified driver.
Then return the original snd-soc-es8316.ko module and write to gpio manually.
I added this systemd unit - /etc/systemd/system/speaker.service 
```

[Unit]
Description = Speakers
After = NetworkManager-wait-online.service network.target network-online.target dbus.service
Wants = NetworkManager-wait-online.service network-online.target
Requires = dbus.service


[Service]
Type = oneshot
ExecStart = /etc/systemd/speakers.sh

[Install]
WantedBy = multi-user.target

```

Where  /etc/systemd/speakers.sh
```

#!/bin/bash
echo 444 > /sys/class/gpio/export
echo out > /sys/class/gpio/gpio444/direction
echo 1 > /sys/class/gpio/gpio444/value

```

then
```

sudo bash 
echo 1 > /sys/class/gpio/gpio444/value
echo 0 > /sys/class/gpio/gpio444/value

```
Turn on / off the speakers.

---

### Post by lisati on 2018-11-06
@urby66:

I've moved your response to this thread to a thread of its own [here]("https://ubuntuforums.org/showthread.php?t=2405488"). Sometimes what appears to be a similar problem with similar hardware can have a different solution.

Old thread closed.

---

