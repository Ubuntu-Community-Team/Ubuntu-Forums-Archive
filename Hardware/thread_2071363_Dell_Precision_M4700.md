---
title: "Dell Precision M4700"
date: 2012-10-15
forum: Hardware
---

### Post by Artpen on 2012-10-15
Hi Guys,
   
  I am very happy because today I’ve received Dell Precision M4700. Of cause I will be installing Ubuntu 12.04!
  And of cause I have some questions ))) and in advance sorry for them.
  I will working with 3d animation and rendering with Blender. So I need to setup my system to be very stable and fast.
   
  Questions about SSD (512Gb) and partitions. There were a lot of discussions about what partitions you need to make, but I think they all slightly dated.
   
  [FONT=Calibri]1.       [/FONT]What partition do I need for the system that I am going to use at least 3-4 years.
  [FONT=Calibri]2.       [/FONT]How to make intelligent partitions so I will be able to reinstall my Linux (Ubuntu) but keep the other partition the same
  [FONT=Calibri]3.       [/FONT]Which file system to use.
  [FONT=Calibri]4.       [/FONT]I have 16Gb of Ram – how much Swap do I need for 3d Rendering system?
   
  Questions about video card:
   
  [FONT=Calibri]5.       [/FONT]Could you please send a link on how to install CUDA and Quadro drivers? 
  [FONT=Calibri]6.       [/FONT]How to make all these more stable? Which drivers to use?
   
  General notes:
  [FONT=Calibri]7.       [/FONT]Who have to use this Laptop (or M4600) Do you have any advises?
   
  Thanks for help.
  I will post my partition as soon as possible so we can discuss it.
   
  Cheers

---

### Post by ALinuxWindowsBalance on 2012-10-15
> **Artpen said:**
> Hi Guys,
   
  I am very happy because today I&#8217;ve received Dell Precision M4700. Of cause I will be installing Ubuntu 12.04!
  And of cause I have some questions ))) and in advance sorry for them.
  I will working with 3d animation and rendering with Blender. So I need to setup my system to be very stable and fast.
   
  Questions about SSD (512Gb) and partitions. There were a lot of discussions about what partitions you need to make, but I think they all slightly dated.
   
  [FONT=Calibri]1.       [/FONT]What partition do I need for the system that I am going to use at least 3-4 years.
  [FONT=Calibri]2.       [/FONT]How to make intelligent partitions so I will be able to reinstall my Linux (Ubuntu) but keep the other partition the same
  [FONT=Calibri]3.       [/FONT]Which file system to use.
  [FONT=Calibri]4.       [/FONT]I have 16Gb of Ram &#8211; how much Swap do I need for 3d Rendering system?
   
  Questions about video card:
   
  [FONT=Calibri]5.       [/FONT]Could you please send a link on how to install CUDA and Quadro drivers? 
  [FONT=Calibri]6.       [/FONT]How to make all these more stable? Which drivers to use?
   
  General notes:
  [FONT=Calibri]7.       [/FONT]Who have to use this Laptop (or M4600) Do you have any advises?
   
  Thanks for help.
  I will post my partition as soon as possible so we can discuss it.
   
  Cheers
Nice computer!

Okay, first up. You're going to need a / partition, that is where it is mounted, the root directory. You also might want partitions for all the mount areas, do it from the Ubuntu installer, you'll see what I mean.

Next. Reinstalling Ubuntu. Unless you are installing a different distro, like Fedora or openSUSE,
all you need to do is use this tool [http://www.diffingo.com/oss/fwbackups](http://www.diffingo.com/oss/fwbackups) and restore whenever you want.

Here is CUDA support, from NVIDIA's home page. [http://developer.download.nvidia.com/compute/cuda/5_0/rel/installers/cuda_5.0.35_linux_64_ubuntu11.10.run](http://developer.download.nvidia.com/compute/cuda/5_0/rel/installers/cuda_5.0.35_linux_64_ubuntu11.10.run)

**WARNING! IT IS CREATED FOR 11.10!!**

Alright, next. Quadro Drivers. Here, you can select your make and model of Quadro, and download drivers. the file extension is .run

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
I don't have that laptop, but the specs are amazing! Unfortunately I don't have a thousand bucks to shell out for a laptop. I prefer workstations, but that's just because I can put in my own motherboard, and stuff.

---

### Post by Tomaok on 2012-10-15
hello,

could you make us a short review of what is working well or not with your fresh install of Ubuntu on this laptop ?

I'm about to buy a 4700 but i wonder if it will work enough with actual driver to do my job
( CAO and linux dev mainly).

for file system look at : [http://superuser.com/questions/228657/which-linux-filesystem-works-best-with-ssd](http://superuser.com/questions/228657/which-linux-filesystem-works-best-with-ssd)

for partition i will take :
20Go for / 
20Go for /home
+ some data partition
for swap it 's a good question, do you really need swap with 16Gb of Ram ??
I don't do 3d anim. so i don't known!

bye

---

### Post by Grigii on 2012-10-16
I have the Precision M4700, running Gentoo Linux. There is several bleeding-edge features on this notebook, but in general it works fantastically :-)

[http://en.gentoo-wiki.com/wiki/Dell_Precision_M4700](http://en.gentoo-wiki.com/wiki/Dell_Precision_M4700)

Also, since you are probably going to use Ubuntu some of the technical advice/info may not apply. If you don't patch your kernel for that touchpad, it will still work as a mouse, but just without multi-touch.

Hope it helps :-)

---

### Post by Tomaok on 2012-10-16
thanks a  lot for your wiki , it's usefull to see that you have no big problem

with the hardware. and your advice on bios conf should be usefull too for every

linux user. i'm a kubuntu one !

---

### Post by Grigii on 2012-10-17
A pleasure.
I always used to read other peoples documentation on Linux glitches for notebooks, so decided to give it a go myself :-)

---

### Post by Tomaok on 2012-10-19
One more question about proposed ddr memory for M4700 :

On dell store we have the choice between 1600 and 1866MHz memory

But Intel i7 processor support memory until 1600 only !

So why Dell sell 1866 and what are the true benefits for the system ??

If someone can tell me ?

have a good day !

---

### Post by Grigii on 2012-10-19
Dell rates the system able of 1866Mhz ram, I think intel's values are guidelines.

Maybe they found a valid reason in some very specific application? Or maybe they just want some premium checkbox feature to differentiate the precision?

Bottom line is I wouldn't go for 1866 unless you are going top-top-spec.

---

### Post by memecs on 2012-10-19
See my post here: [http://ubuntuforums.org/showthread.php?t=2073224](http://ubuntuforums.org/showthread.php?t=2073224)

Nvidia drivers are not working to me...

---

### Post by Artpen on 2012-11-04
Guys Thanks for you replies!

Laptop is working fine. After installing Ubuntu 12.04 a had a problem with Nvidia!!
[http://ubuntuforums.org/showthread.php?t=2073224](http://ubuntuforums.org/showthread.php?t=2073224)
This link was very helpful.
But sometimes I still dont understand what I am doing while installing video drivers:confused:
Thanks for help.

[Tomaok]("http://ubuntuforums.org/member.php?u=1691387")
I took my Dell with 1600 ram. I have 2Gb plates 1833 at home. I tried to install it but Laptop is recognising it like 1600


Best

---

### Post by Tomaok on 2012-11-12
thanks for your reply Artpen

I ve chosen 1600 and your comment tell me it 's a good choice.

For nvidia installation, i've done this simple things :
- at X login screen (kdm) i did MENU then console login
- then remove  nouveau driver  with rmmod nouveau
- then execute .run from nvidia
- then i've wrote the conf file to disable nouveau like nvidia explain it to do
- then reboot and disable optimus

that's all and now i can use all my display ports !

By the way, i 've this computer since 4 days and i'm very happy
it 's a big jump from my 6 years old latitude d810

bye

---

### Post by Askel on 2012-12-16
I've got a M4600 with Quadro K2000M. 

Have you got everything to work with you M4700? Like HDMI and displayport?

I can't get either the displayport or the HDMI to work. Did you use the Nvidia-drivers from Ubuntu (additional drivers) or Nvidias native from their website? If so, how complicated was the install?

//Askel

---

### Post by LegendaryFury on 2013-05-21
The touchpad for an M4700 does not work by default either. The instructions in the following post got it working for me: [http://askubuntu.com/questions/50491/detect-touchpad-as-touchpad/258513#258513](http://askubuntu.com/questions/50491/detect-touchpad-as-touchpad/258513#258513)

---

