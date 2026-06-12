---
title: "Sound blaster Z Linux test-patch"
date: 2016-05-28
forum: Hardware
---

### Post by hhh81 on 2016-05-28
[http://forums.creative.com/showthread.php?t=741501](http://forums.creative.com/showthread.php?t=741501)

This works to me, line out ,front left and front right.   mic in 1st jack.  in ubuntu 16.4 x64. I have Sb z.
but not rear left and rear right.  and no front panel for mic and headphones.

---

### Post by hhh81 on 2016-05-29
i want to know how to keep the patch modify (changes/improvements) when will be out the next kernel.

---

### Post by jeremy31 on 2016-05-29
Did you apply the patch to kernel source code?  Or just download the kernel from dropbox?

---

### Post by hhh81 on 2016-05-29
I have used and installed the .deb files from dropbox

linux-image-4.5.0-sbz_4.5.0-sbz-1_amd64.deb  
linux-headers-4.5.0-sbz_4.5.0-sbz-1_amd64.deb

---

### Post by jeremy31 on 2016-05-29
By using that you may put your system at risk because the kernel will update but not be used after rebooting since that kernel is 4.5 which is higher than the 4.4 kernels used by 16.04

---

### Post by hhh81 on 2016-05-29
What should i do?   Use ubuntu without audio ?

---

### Post by jeremy31 on 2016-05-29
I have manually added the patch to 4.4 source code, compiled it and installed it in my kernel modules and nothing bad has happened.  I do not have the sound blaster z
Post the result of ```
ls /lib/modules
``` and I will see if I can compile the modules for a 4.4 kernel that you have for a test

---

### Post by hhh81 on 2016-05-29
user@user-System-Product-Name:~$ ls /lib/modules
4.4.0-22-generic  4.5.0-sbz

thank you.

---

### Post by jeremy31 on 2016-05-29
You will need to boot into the 4.4.0-22 kernel before starting, use the Grub menu through Advanced Options to select the kernel


First we will make a new directory and make copies of the modules
```
mkdir sound
cp /lib/modules/4.4.0-22-generic/kernel/sound/pci/hda/*.ko sound/
```

Now to install some packages to compile
```
sudo apt-get install git linux-headers-generic build-essential
```

Clone the source code I put on github
```
git clone https://github.com/jeremyb31/4.4sound-blaster-z.git
cd 4.4sound-blaster-z
```
Copy some system files so they work

```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
cp /usr/src/linux-headers-$(uname -r)/.config ./
```

Finally to build the modules and copy them to the correct directory
```
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/
```

Now you can reboot back to the 4.4.0-22 to test

---

### Post by hhh81 on 2016-05-29
when i'll update to next kernel what commands should i do?

---

### Post by jeremy31 on 2016-05-29
When a new kernel is loaded then you would do
```
cd 4.4sound-blaster-z
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
cp /usr/src/linux-headers-$(uname -r)/.config ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/
```

Or the commands could be made into a script

---

### Post by hhh81 on 2016-05-29
doesn't work, no audio.

---

### Post by jeremy31 on 2016-05-29
Ok, if I find something else, I will post again.  There must be something else missing in the 4.4 source.  Thanks for trying it

Try the instructions from post 9 again, I was able to compile using the original patched file

---

### Post by hhh81 on 2016-05-30
I tried again and is not changed. no audio.

---

### Post by hhh81 on 2016-05-30
You can see this image, above is how is audio panel in kernel 4.4.0-22-generic,  and below is how it is in 4.5.0-sbz kernel .

same image here [http://postimg.org/image/cdqd9qktn/](http://postimg.org/image/cdqd9qktn/)
not resized/compressed

---

### Post by hhh81 on 2016-05-31
Who can help me?   When will be out a next kernel?  We don't know what to do to patch with this modify.

---

### Post by jeremy31 on 2016-06-01
I am exchanging emails with the person who made the patch to see if and how the 4.4 Ubuntu kernel can be patched.  It would be easier if they didn't have the entire Linux kernel on github as I am on a download limit on internet

Keep using the 4.5 modified kernel if you need the sound to work

---

### Post by jeremy31 on 2016-06-03
Lets try one more time with the 4.4 kernel
```
cd cd 4.4sound-blaster-z
git pull
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
cp /usr/src/linux-headers-$(uname -r)/.config ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/
```

Reboot and see.  I this doesn't work I will have to give up and I don't know what else to do.  I tried compiling using source code from 4.5 with 4.4 kernel headers and it doesn't work

---

### Post by hhh81 on 2016-06-03
cd cd 4.4sound-blaster-z   >  i think it should be  cd 4.4sound-blaster-z

I tried and doesn't work.

---

### Post by hhh81 on 2016-06-03
user@user-System-Product-Name:~/4.4sound-blaster-z$ sudo git pull
[sudo] password for user: 
Updating 79b84ec..73b958d
error: Your local changes to the following files would be overwritten by merge:
	.config
Please, commit your changes or stash them before you can merge.
Aborting

---

### Post by jeremy31 on 2016-06-03
Did the git pull command show any response indicating new files were downloaded?

---

### Post by hhh81 on 2016-06-03
No, only that text.

---

### Post by jeremy31 on 2016-06-03
Have to try it a different way
```
rm -rf 4.4sound-blaster-z
git clone https://github.com/jeremyb31/4.4sound-blaster-z.git
cd 4.4sound-blaster-z
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
cp /usr/src/linux-headers-$(uname -r)/.config ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/
```

---

### Post by hhh81 on 2016-06-03
```
enrico@enrico-System-Product-Name:~$ rm -rf 4.4sound-blaster-z

```
```
enrico@enrico-System-Product-Name:~$ git clone [https://github.com/jeremyb31/4.4sound-blaster-z.git](https://github.com/jeremyb31/4.4sound-blaster-z.git)

Cloning into '4.4sound-blaster-z'...
remote: Counting objects: 53, done.
remote: Compressing objects: 100% (47/47), done.
remote: Total 53 (delta 9), reused 48 (delta 6), pack-reused 0
Unpacking objects: 100% (53/53), done.
Checking connectivity... done.
```

```
enrico@enrico-System-Product-Name:~$ cd 4.4sound-blaster-z

enrico@enrico-System-Product-Name:~/4.4sound-blaster-z$ cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers

enrico@enrico-System-Product-Name:~/4.4sound-blaster-z$ cp /usr/src/linux-headers-$(uname -r)/.config ./

enrico@enrico-System-Product-Name:~/4.4sound-blaster-z$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make: Entering directory '/usr/src/linux-headers-4.4.0-22-generic'
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_bind.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_codec.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_jack.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_auto_parser.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_sysfs.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_controller.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_proc.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_hwdep.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_beep.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec.o
  CC [M]  /home/enrico/4.4sound-blaster-z/hda_generic.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-generic.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_realtek.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-realtek.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_cmedia.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-cmedia.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_analog.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-analog.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_sigmatel.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-idt.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_si3054.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-si3054.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_cirrus.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-cirrus.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_ca0110.o
  LD [M]  /home/enrico/4.4sound-blaster-z/snd-hda-codec-ca0110.o
  CC [M]  /home/enrico/4.4sound-blaster-z/patch_ca0132.o
In file included from /home/enrico/4.4sound-blaster-z/patch_ca0132.c:30:0:
/home/enrico/4.4sound-blaster-z/patch_ca0132.c:4777:53: error: ‘CA0132_GEN_FIXUP_SBZxR’ undeclared here (not in a function)
  SND_PCI_QUIRK(0x1102, 0x0033, "Sound Blaster ZxR", CA0132_GEN_FIXUP_SBZxR),
                                                     ^
include/sound/core.h:429:43: note: in definition of macro ‘SND_PCI_QUIRK’
  {_SND_PCI_QUIRK_ID(vend, dev), .value = (val)}
                                           ^
scripts/Makefile.build:258: recipe for target '/home/enrico/4.4sound-blaster-z/patch_ca0132.o' failed
make[1]: *** [/home/enrico/4.4sound-blaster-z/patch_ca0132.o] Error 1
Makefile:1396: recipe for target '_module_/home/enrico/4.4sound-blaster-z' failed
make: *** [_module_/home/enrico/4.4sound-blaster-z] Error 2
make: Leaving directory '/usr/src/linux-headers-4.4.0-22-generic'

enrico@enrico-System-Product-Name:~/4.4sound-blaster-z$ sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/
cp: cannot stat '*.ko': No such file or directory
```


I have to reboot now ?

---

### Post by jeremy31 on 2016-06-03
Try it again as I took care of the line that caused the issue
```
rm -rf 4.4sound-blaster-z
git clone https://github.com/jeremyb31/4.4sound-blaster-z.git
cd 4.4sound-blaster-z
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
cp /usr/src/linux-headers-$(uname -r)/.config ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp *.ko /lib/modules/$(uname -r)/kernel/sound/pci/hda/

```

---

### Post by hhh81 on 2016-06-03
I have rebooted and audio doesn't work

---

### Post by jeremy31 on 2016-06-03
Will have to wait on emails then.  I linked this thread in the last one

---

### Post by olci on 2016-06-24
Hi, 
i tried with test-patch with correct pin configs copied from working freebsd/windowz driver for my card 1102:0023 but no sound 
yes freebsd_11 works fine with ca0132 but linux doesn't work :) 

[https://bugzilla.kernel.org/show_bug.cgi?id=120491](https://bugzilla.kernel.org/show_bug.cgi?id=120491)

---

### Post by fredd2 on 2016-11-16
Here are my findings with the Sound Blaster Z card on Linux Mint 18 64-bit with the stock 4.4 kernel. Both input and output can be made to work without installing anything special at the moment.

**How to make output work:**

Right now only output seems to come out of the front panel port. So ensure the audio header of your computer case is connected to the sound card. Be certain not to connect it to the motherboard sound card. Open a terminal and in there open alsamixer. You can select your card by pressing F6. Then you can press F5 to display all options. Be sure HP/Speaker is enabled. You can toggle options with the M key on your keyboard, and the arrow keys as well. All audio output enhancements work.

**How to make input work:**

Input only works via the microphone port in the back. With alsamixer (see above) you can configure options. You can use the M key to toggle options, and the keys ; and # allow you to enable left and right configurations. Arrow keys can be used to set sliders.

**Conclusion:**

So things are working fine, audio enhancements, voice clarity, voice transformation, and so forth can all be set via alsamixer, only the ports are a mess. I hope this helps both developers and users. Here is a picture of my setup. I am only using headphones right now as I would require an extension cable to plug in the microphone in the back:

[[IMG]http://i.imgur.com/OosqrER.png[/IMG]]("http://i.imgur.com/OosqrER.png")

I have also posted my findings to the ALSA development mailing list: [http://mailman.alsa-project.org/pipermail/alsa-devel/2016-November/114864.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2016-November/114864.html)

---

### Post by shspvr on 2017-02-15
> **fredd2 said:**
> Here are my findings with the Sound Blaster Z card on Linux Mint 18 64-bit with the stock 4.4 kernel. Both input and output can be made to work without installing anything special at the moment.

**How to make output work:**

Right now only output seems to come out of the front panel port. So ensure the audio header of your computer case is connected to the sound card. Be certain not to connect it to the motherboard sound card. Open a terminal and in there open alsamixer. You can select your card by pressing F6. Then you can press F5 to display all options. Be sure HP/Speaker is enabled. You can toggle options with the M key on your keyboard, and the arrow keys as well. All audio output enhancements work.

**How to make input work:**

Input only works via the microphone port in the back. With alsamixer (see above) you can configure options. You can use the M key to toggle options, and the keys ; and # allow you to enable left and right configurations. Arrow keys can be used to set sliders.

**Conclusion:**

So things are working fine, audio enhancements, voice clarity, voice transformation, and so forth can all be set via alsamixer, only the ports are a mess. I hope this helps both developers and users. Here is a picture of my setup. I am only using headphones right now as I would require an extension cable to plug in the microphone in the back:


I have also posted my findings to the ALSA development mailing list: [http://mailman.alsa-project.org/pipermail/alsa-devel/2016-November/114864.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2016-November/114864.html)

I wish they change it to SB Core3D in stead of SB Recon3D 

Hi just wonder did you ever fig out how get S/PDIF input working ?
The Input level is move but I have no sound

---

### Post by Margus1 on 2017-03-12
Yeah HP Speaker have to enable works with old linux versions also not only with new ones GNOME ALSA Mixer is so easy to use and save alsamixer conf later after HP selected i know this trick back to 2013 with recon 3d

---

### Post by shspvr on 2017-03-16
> **Margus1 said:**
> Yeah HP Speaker have to enable works with old linux versions also not only with new ones GNOME ALSA Mixer is so easy to use and save alsamixer conf later after HP selected i know this trick back to 2013 with recon 3d
Thanks I have look get that app install

---

### Post by shspvr on 2017-03-19
> **Margus1 said:**
> Yeah HP Speaker have to enable works with old linux versions also not only with new ones GNOME ALSA Mixer is so easy to use and save alsamixer conf later after HP selected i know this trick back to 2013 with recon 3d
Sad part is I still have no working [COLOR=#000000]S/PDIF input BooHoo [/COLOR]

---

### Post by l5d on 2017-11-30
Bonjour,
la méthode donnée par jeremy31 a fonctionné sur mon matériel Creative Sound Blaster Z sous Linux Mint 17.3 rosa 64 bits Cinnamon, avec le patch sur le noyau 4.4.0-22

Hello,
This proccess describe by jeremy31 has been successful form my computer. Great Thank to it.:) i get sound on HP line, rear jack on the board Creative Sound Blaster Z.

---

### Post by qraxin on 2017-12-18
Hello!
I have the same problem. I have **Creative Sound Blaster Z** and there is no sound in Linux.
I installed **Linux Mint 18 Srah based on Ubuntu 16.04** with Kerenel version of **4.4.0-21**. And after I made solution from jeremy31 posts, I got a sound from my card.
But, I dont need the Linux Mint, I want to work on Ubuntu.
After that, I installed **Ubuntu 16.04**, with the same **Kernel 4.4.0-21** and did the same actions. But the sound don`t work!
I don`t understand how it is possible. I guess, that Linux Mint have other software unlike Ubuntu.
Can some help me?

---

### Post by oldos2er on 2017-12-18
@qraxin Please start a new thread for your question; it's unlikely anyone will see your post because this thread is getting old.

---

### Post by fredd2 on 2018-01-17
I can only get audio by connecting it to the headphone port on my case. You do have to make sure your case's audio header cable is connected to the sound card.

You will also have to enable headphone jack detection in alsamixer. Then if you boot the system, plug the cable (take it out and plug it in again if already inserted) and you should have audio.

---

### Post by shspvr on 2018-03-12
Well I final got it end order to enable S/PDIF open a terminal and run "pactl load-module module-loopback"
Now I have S/PDIF input
What suck is Ubuntu 17.?? and 18.?? are use less with the HP/Speaker which is enabled but no sound what so ever

---

