---
title: "How do I Install Drivers for Nvidia Geforce GTX 660Ti?"
date: 2013-05-29
forum: Hardware
---

### Post by Hyper Tails on 2013-05-29
Hey guys;

I have just received my Nvidia Geforce GTX 660 Ti graphics card from Newegg, I installed it and played around with it on my Windows 8 box before I installed its drivers on my Ubuntu 13.04 box.

I tried downloading the drivers from Nvidia's site, but every-time I try to run the installation, I keep getting a message saying "You have X server running". I pressed Ctrl+Alt+F1 to try that and it gave me the same message.

I tried another way from this site: [http://linuxg.net/nvidia-319-23-has-been-released-how-to-install-nvidia-319-23-drivers-on-linux/](http://linuxg.net/nvidia-319-23-has-been-released-how-to-install-nvidia-319-23-drivers-on-linux/)
and I just get a blank screen with an blinking line.

Any help will be thanked.

---

### Post by D0natell0 on 2013-05-29
This task has become much easier since 12.04. This solution assumes you're running the Unity desktop.
- click on system-settings>additional drivers
- wait for available drivers to load
- click on nvidia accelerated driver (version current), activate
HTH.

---

### Post by Hyper Tails on 2013-05-29
To be honest, there is no additional drivers listed in my software sources....

What should I do to get some drivers to show up?

---

### Post by papibe on 2013-05-29
Hi Hyper Tails.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

apt-cache policy nvidia-current

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i9'
```
Regards.

BTW, just to be precise: in 13.04 the steps are the following: open 'Software & Updates', and go to the tab called 'Additional Drivers'.

---

### Post by Hyper Tails on 2013-05-29
> **papibe said:**
> Hi Hyper Tails.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

apt-cache policy nvidia-current

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i9'
```
Regards.

BTW, just to be precise: in 13.04 the steps are the following: open 'Software & Updates', and go to the tab called 'Additional Drivers'.
```

liam@liam-Z68P-DS3:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 660 Ti] [10de:1183] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3660]
	Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3660]
	Kernel driver in use: snd_hda_intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
liam@liam-Z68P-DS3:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 304.88-0ubuntu1
  Version table:
     304.88-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted amd64 Packages
liam@liam-Z68P-DS3:~$ 
liam@liam-Z68P-DS3:~$ lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i9'
nouveau               939088  3 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_hda_intel          39619  10 
i915                  600351  1 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mxm_wmi                13021  1 nouveau
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
wmi                    19070  2 mxm_wmi,nouveau
ghash_clmulni_intel    13259  0 
ttm                    83187  1 nouveau
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
video                  19390  2 i915,nouveau
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
xts                    12885  1 aesni_intel
drm_kms_helper         49394  2 i915,nouveau
lrw                    13257  1 aesni_intel
drm                   286313  7 ttm,i915,drm_kms_helper,nouveau
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i2c_algo_bit           13413  2 i915,nouveau
snd                    68876  36 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
liam@liam-Z68P-DS3:~$ 

```

Here they are; I know ablout the Software & Updates drivers (That's where I went too)

---

### Post by papibe on 2013-05-29
Thanks.

There it is:
```

liam@liam-Z68P-DS3:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [**GeForce GTX 660 Ti**] [10de:1183] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3660]
	Kernel driver in use: nouveau
```
I can't really say why it is not offer in 'Additional Drivers', but we can install it manually.

Open a terminal, and run this commands:
```
sudo apt-get install nvidia-current

sudo nvidia-xconfig
```
Then restart your machine.

The worst case scenario is that you boot into a black screen. Avoid pressing your power button to restart or power down your machine. Instead, you can get into a text-mode console by pressing Ctrl+Alt+F1 (or F2). You can login there using your regular user. There you can restart by running:
```
sudo reboot
```
and turn it off by running:
```
sudo poweroff
```
In any case, booting into a black screen using the Nvidia driver may indicate that your card does not support the kernel mode. To allow compatibility set the flag 'nomodeset' on the grub options.

While in text mode, edit this file:
```
sudo nano /etc/defualt/grub
```
Look for a like that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add nomodeset to it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file, and reboot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Hyper Tails on 2013-05-29
I did everythingyou said, I rebooted, and got my login screen to show up like normal. I finally got some more driver options to show up; I selected the recommend driver. I rebooted again and got,my login screen again, and fires up Portal via Steam, and it worked the way it should, no input delay and everything's running smoothly.

Thanks for your help guys!! :-)

---

