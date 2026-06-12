---
title: "Toshiba U500 nVidia no Brightness control"
date: 2010-05-06
forum: Hardware
---

### Post by strikoo on 2010-05-06
Hi! ):P

Ubuntu 10.04 x64
Toshiba u500-17f
intel c2d p7450 on intel gm45
nVidia g210m

Graphics card works fine, compiz effects are working with nVidia driver, but problem is with brightness control.
On windows to enable brightness control, in driver inf is added registry dword key EnableBrightnessControl=1, if that key doesn't exist, the brightness control doesn't work so,
I find that there is no EnableBrightnessControl in /proc/drivers/nvidia/registry. My thinking is if I manage to add it there that brightness will work, the problem is that I don't know how to add it there.

Function keys FN+F6-F7 work, when I press them the brightness slider is shown and moving.

Thanks

---

### Post by ghepeath on 2010-05-07
Hey i'm having the same problem, with my Toshiba M505 series

---

### Post by juju27 on 2010-05-07
I have a Toshiba U500. I had the same problem. 
Following some threads, I tried to add registry dword key EnableBrightnessControl=1 by adding the line into the "Device" section of /usr/X11/xorg.conf file
 Option "RegistryDwords" "EnableBrightnessControl=1". But it didn't work. I don't know why.

But very recently, a little driver was proposed to solve the same problem on sony laptop. 
Following the thread  [http://www.nvnews.net/vbulletin/showthread.php?t=143025](http://www.nvnews.net/vbulletin/showthread.php?t=143025), I now can change the brightness (backlight) level :-). Now I can remove my sunglasses to work on my laptop ;-)
However, it is not a plug and play installation. Several modifications have to be done in order to get it work especially if you want that the power-manager control the backlight level. To work with Toshiba laptop, I had to add one line in the source code (see juju321's post).  
If you have some difficulty, I can try to explain step by step the installation.

Juju27

PS. my system is Ubuntu 9.10 32 bits and the F6-F7 function keys are still not working.

---

### Post by strikoo on 2010-05-08
Thank you!
I will give this a try and report here.
My function keys are working in 10.04 x64 but no effect on backlight.

---

### Post by juju27 on 2010-05-08
This is how I did it

First download the nvidia-bl-dkms 0.16.7 package on Mactel ([https://launchpad.net/~mactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all]("https://launchpad.net/%7Emactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all"))
that corresponds to your distribution.
Install the package.
Then go to 
/usr/src/nvidia_bl-0.16.7 directory.
sudo dkms remove -m nvidia_bl -v 0.16.7 --all
Then edit nvidia-bl.c and add "PCI_VENDOR_ID_TOSHIBA" to static const unsigned nvidia_bl_subvendors[] __initdata (line 472)

then sudo dkms add -m nvidia_bl -v 0.16.7
sudo dkms build -m nvidia_bl -v 0.16.7
sudo dkms install -m nvidia_bl -v 0.16.7

The driver is loaded by
sudo modprobe nvidia_bl max_level=0x100000 shift=8
With this setting, the maxium level is 512

Now you can test the driver 
cat /sys/class/backlight/nvidia_backlight/brightness
shows the level
echo 200 | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness
sets the level to 200

Now to load the driver at each boot,
add nvidia_bl to last line of /etc/modules
create the text file nvidia_bl.conf with the line 
     options nvidia_bl max_level=0x20000 shift=8
in it.

Finally, to be used with the gnome-power-manager, we have to hide the other way (that does not work) to gnome.
It happens if when you type "ls /sys/class/backlight/"
you have another folder than nvidia_backlight. 
In my case for instance, acpi_video0.
To hide it, add 
Create the file /etc/hal/fdi/preprobe/toshiba.fdi and paste the following text
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

<device>
<!-- Ignore backlight interface created by sony_laptop
-->
<match key="linux.sysfs_path" string="/sys/devices/virtual/backlight/video0">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>
Now you restart, and then you could change the backlight level with the gnome-power applet

PS.
Be careful to remove, if it exists, the line "Option "RegistryDwords" "EnableBrightnessControl=1" from /etc/X11/xorg.conf from the device section. Otherwise there are some conflicts.

---

### Post by strikoo on 2010-05-09
thank you for the help. The brightness control now works but not right.

The gnome slider for brightness doesn't go all the way up or down. I only get 4 steps...

---

### Post by juju27 on 2010-05-10
Good.
I omitted to say that the file nvidia_bl.conf has to be created in /etc/modprobe.d/
To check if the setting is ok when you type
cat /sys/class/backlight/nvidia_backlight/max_brightness
you should obtain 512?
If you get this value but it is still not working with the powe-manager slide, first test with command line
echo 200 | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness
Change 200 into 300, etc till 512
If you have a progressive light changing it is not a problem of the driver. If yes, it sounds like, the maximum value is not good, then you have to find it manually.
To that end
first 
sudo rmmod nvidia_bl          (this is for unloading the driver)
then 
sudo modprobe nvidia_bl max_level=0x100000
then
echo $((0x100000)) | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness
decrease $((0x100000)), and play with the value to find the maximum value.
Be careful, if the value is too small the screen light is off!
When you have it you have to choose the shift value. To find it you can use the calculator tool. Choose hex, devide the maximum value by 0x200 than select bit and count the number of digit. This number is the shift value.
You can test the config with 
sudo rmmod nvidia_bl
sudo modprobe nvidia_bl max_level=your value shift=your value
and
cat /sys/class/backlight/nvidia_backlight/max_brightness
will give you the maximum value seen by the slider (it should be lower than 2048)
and you can test it  with
echo your value | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness
Finally modify the values in nvidia_bl.conf

That's it ;-)

---

### Post by strikoo on 2010-05-10
Thank you for helping. It seams that the problem is in the slider or gnome applet...
When I go to power options on battery on AC tab the slider works just fine. Only the FN+F6-F7 slider makes problems. It seams to be stuck on last 4 steps. Max value (512) - 4 steps.

I will check your latest post in the morning. tnx

---

### Post by toogooda on 2010-05-11
> **juju27 said:**
> This is how I did it

First download the nvidia-bl-dkms 0.16.7 package on Mactel ([https://launchpad.net/~mactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all]("https://launchpad.net/%7Emactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all"))
that corresponds to your distribution.
Install the package.
Then go to 
/usr/src/nvidia_bl-0.16.7 directory.
sudo dkms remove -m nvidia_bl -v 0.16.7 --all
Then edit nvidia-bl.c and add "PCI_VENDOR_ID_TOSHIBA" to static const unsigned nvidia_bl_subvendors[] __initdata (line 472)

then sudo dkms add -m nvidia_bl -v 0.16.7
sudo dkms build -m nvidia_bl -v 0.16.7
sudo dkms install -m nvidia_bl -v 0.16.7

The driver is loaded by
sudo modprobe nvidia_bl max_level=0x100000 shift=8
With this setting, the maxium level is 512

Now you can test the driver 
cat /sys/class/backlight/nvidia_backlight/brightness
shows the level
echo 200 | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness
sets the level to 200

Now to load the driver at each boot,
add nvidia_bl to last line of /etc/modules
create the text file nvidia_bl.conf with the line 
     options nvidia_bl max_level=0x20000 shift=8
in it.

Finally, to be used with the gnome-power-manager, we have to hide the other way (that does not work) to gnome.
It happens if when you type "ls /sys/class/backlight/"
you have another folder than nvidia_backlight. 
In my case for instance, acpi_video0.
To hide it, add 
Create the file /etc/hal/fdi/preprobe/toshiba.fdi and paste the following text
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

<device>
<!-- Ignore backlight interface created by sony_laptop
-->
<match key="linux.sysfs_path" string="/sys/devices/virtual/backlight/video0">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>
Now you restart, and then you could change the backlight level with the gnome-power applet

PS.
Be careful to remove, if it exists, the line "Option "RegistryDwords" "EnableBrightnessControl=1" from /etc/X11/xorg.conf from the device section. Otherwise there are some conflicts.

I got so excited but no it didn't work for me even though the source code in the .c file included my card type :(

It all worked until i started the driver

```
sudo modprobe nvidia_bl max_level=0x100000 shift=8
```then my screen changed to about 10% back-light and flickered badly for a min or two before turning the back-light off completely. To my relief it was back to normal after a reboot!

I repeated the process carefully and sure the second time I made no mistakes but alas the same issue :(

I have a Toshiba Qosmio G40 with a 8600 GT card.

Could it be a clash with the hack I did to get sound and mic working?

     Code:
     sudo gedit /etc/modprobe.d/alsa-base.conf 
 add the following line to the bottom of the page
      Code:
     options snd-hda-intel model=hp-bpc 
do I put hp-bpc instead of Toshiba in the .c file ( I doubt it)

Any Ideas?

PS I should also note that I am using a 64bit version of Ubuntu 10.4 and the driver download was 32 bit, but I have used many 32 bit items without issue and there was no compile issues or errors.

---

### Post by juju27 on 2010-05-11
I don't think it is a problem linked to your hack. Also I don't think to put hp-bpc instead of Toshiba in the .c file solve the problem.
Some ideas 
- My nvidia chip is different. It is g210m. Maybe the maximum value  for the 8600 GT is very different. Try "sudo modprobe nvidia_bl" alone. The default setting is maybe the good one. 
- My ubuntu is 32 bits. It works almost perfectly. Only the Fn keys do not work. Strikoo has also some problems with ubuntu 64 bits. Wait some news from him. Maybe it is releated to 64 bits? See on another forum or threads with an issue with mactel package?
- Be careful to remove, if it exists, the line "Option "RegistryDwords" "EnableBrightnessControl=1" from /etc/X11/xorg.conf from the device section. Otherwise there are some conflicts.

From now, it is the only ideas I have.

---

### Post by toogooda on 2010-05-12
> **juju27 said:**
> I don't think it is a problem linked to your hack. Also I don't think to put hp-bpc instead of Toshiba in the .c file solve the problem.
Some ideas 
- My nvidia chip is different. It is g210m. Maybe the maximum value  for the 8600 GT is very different. Try "sudo modprobe nvidia_bl" alone. The default setting is maybe the good one. 
- My ubuntu is 32 bits. It works almost perfectly. Only the Fn keys do not work. Strikoo has also some problems with ubuntu 64 bits. Wait some news from him. Maybe it is releated to 64 bits? See on another forum or threads with an issue with mactel package?
- Be careful to remove, if it exists, the line "Option "RegistryDwords" "EnableBrightnessControl=1" from /etc/X11/xorg.conf from the device section. Otherwise there are some conflicts.

From now, it is the only ideas I have.

Juju27 you are the man! 
```
sudo modprobe nvidia_bl
```
worked great, set it to full brightness.

I will try the rest of your instructions now

---

### Post by strikoo on 2010-05-12
> **juju27 said:**
> Strikoo has also some problems with ubuntu 64 bits. Wait some news from him. Maybe it is releated to 64 bits? See on another forum or threads with an issue with mactel package?

I have nothing to add. There are some issues with FN buttons, and on battery because of that I cannot increase brightness or decrease depending on what option I choose in power options.
To bad the brightness applet doesn't work too. Only thing that works for me is the slider in power options that has no function on battery...
Today an update for nvidia_bl has been released. Will look in to it later.
EDIT:
```
http://launchpadlibrarian.net/48279380/nvidia-bl-dkms_0.16.8~lucid_i386.changes
```
> Description: 
 nvidia-bl-dkms - Supplementary Nvidia laptop display backlight support
Changes: 
 nvidia-bl-dkms (0.16.8~lucid) lucid; urgency=low
 .
   * Fixed missing comma
   * **[COLOR="Red"]Added Toshiba to list of supported subvendors[/COLOR]**.


@Juju 
Thank you so much for the helping with this issue.
Does your touch pad scrolling function work?
How did you solve the issue with overheating? acpi.power_nocheck?
How about bluetooth? I used omnibook kernel to enable it.
Any other tips with u500?
tnx

---

### Post by juju27 on 2010-05-13
I sent an email to the developer nvidia-bl to suggest he adds Toshiba to the list of manufacturers.
Thus, It seems, he added it to the list. Does the update work well?
About the touchpad, I do not use it because it is too much sensitive, I use an optical mouse.
Yes I solved the problem of overheating with acpi.power_nocheck. I works well.
Thank you for the bluetooth. I saw the omnibook solution but it is said to only work with toshiba and ambios bios. Because the bios of my u500 is american megatrand I was thinking, the driver was not the good one. But yesterday I installed it and now bluettoh works perfectly :-).
The other tips is for the wifi connection. The wifi was not natively supported by ubuntu 9.10. I installed manually the with rtl8192se_linux_2.6 library. The wifi works good.

---

### Post by strikoo on 2010-05-14
> **juju27 said:**
> I sent an email to the developer nvidia-bl to suggest he adds Toshiba to the list of manufacturers.
Thus, It seems, he added it to the list. Does the update work well?
About the touchpad, I do not use it because it is too much sensitive, I use an optical mouse.
Yes I solved the problem of overheating with acpi.power_nocheck. I works well.
Thank you for the bluetooth. I saw the omnibook solution but it is said to only work with toshiba and ambios bios. Because the bios of my u500 is american megatrand I was thinking, the driver was not the good one. But yesterday I installed it and now bluettoh works perfectly :-).
The other tips is for the wifi connection. The wifi was not natively supported by ubuntu 9.10. I installed manually the with rtl8192se_linux_2.6 library. The wifi works good.

I have AMI (american megatrand) bios too. I saw it was for phoenix bios but I tried it anyway and it works. good for us :P.
My wifi is atheros based and it works out of the box on 10.04.

on nvidia_bl subject
the update works. I don't see any difference except now we don't need to edit source file...
tnx for the replay

---

