---
title: "Ubuntu on Thinkpad T530 with Nvidia Optimus"
date: 2012-06-23
forum: Hardware
---

### Post by yamagami on 2012-06-23
In the next few months I'm thinking to upgrade my trusty Thinkpad T61p to what is today's equivalent: the Thinkpad T530 with the Nvidia graphics chip (NVIDIA Optimus Graphics (NVS 5400M, 1GB))
My main reason for sticking with the Nvidia Thinkpad is its ability to reach very high resolution (1600 x 900) on a non-glare screen. [The exact model spec is here]("http://shop.lenovo.com/SEUILibrary/controller/e/gbweb/LenovoPortal/en_GB/catalog.workflow:item.detail?GroupID=240&Code=T530BEST&category-id=07C01632841E20EC7F6D436EE7AE81ED") 

However, I understand there are some 'issues' with Nvidia Optimus and Linux. Is anyone running Ubuntu on that particular Thinkpad model? Will it work at all, or will it work with some compromises? Any experiences will be appreciated

Thanks
Harel

---

### Post by Gink on 2012-06-26
I've also got my eye on the T530, was hoping to avoid the possible issues by just using the intel HD 4000 graphics, until I realized Lenovo won't let you pick a quad core i7 without adding the Nvidia graphics, so now I'm trying to choose between a lower powered dual core, or adding $ and possible issues with the optimus.

I've seen the 5400m listed in latest nvidia drivers for 12.04, but haven't been able to find specific info on how well it works or support in bumblebee or anything.

---

### Post by AndrewX192 on 2012-06-27
> **Gink said:**
> 
I've seen the 5400m listed in latest nvidia drivers for 12.04, but haven't been able to find specific info on how well it works or support in bumblebee or anything.

The official drivers don't support optimus. If you want to use your dedicate card, you must use bumblebee.

---

### Post by papibe on 2012-06-27
Some Thinkpads have the ability to select the graphics from the BIOS.

Some only allow you to disable the discrete card, but others even let you select either integrated, discrete, or NVIDIA Optimus.

Regards.

---

### Post by Gink on 2012-06-27
> **papibe said:**
> Some Thinkpads have the ability to select the graphics from the BIOS.

Some only allow you to disable the discrete card, but others even let you select either integrated, discrete, or NVIDIA Optimus.

Regards.

So chances are a ThinkPad will have some sort of hardware/bios option to at the very least disable the nvidia card and run the integrated? That's really all I'd need, as long as the having both doesn't cause any problems, and preferably to be able to just use the intel HD 4000 in ubuntu.

---

### Post by EricCBoston on 2012-06-30
Hello,

I recently bought a FHD version of the Lenovo T530 that has Optimus, and I had no trouble installing Ubuntu 12.04 on it. So far I used GoogleEarth and played a couple of Youtube videos without any problems. I am typing this reply on the laptop using Ubuntu.

The BIOS has two options for Optimus.  One selects Optimus, Discrete, or Integrated graphics. The other enables the BIOS to check if the OS supports Optimus and will select Integrated if Optimus is not supported.

I checked after the install, and found my laptop is set to Optimus, and the OS check is disabled! This is the setting from the factory. The lsmod output lists both i915 and nouveau drivers loaded. I assume it is only using the i915 drivers.

I have not done any experiments or benchmarking. It does seem faster than my old T61.

73 Eric

---

### Post by jbblack on 2012-07-07
> **EricCBoston said:**
> Hello,

I recently bought a FHD version of the Lenovo T530 that has Optimus, and I had no trouble installing Ubuntu 12.04 on it. So far I used GoogleEarth and played a couple of Youtube videos without any problems. I am typing this reply on the laptop using Ubuntu.

The BIOS has two options for Optimus.  One selects Optimus, Discrete, or Integrated graphics. The other enables the BIOS to check if the OS supports Optimus and will select Integrated if Optimus is not supported.

I checked after the install, and found my laptop is set to Optimus, and the OS check is disabled! This is the setting from the factory. The lsmod output lists both i915 and nouveau drivers loaded. I assume it is only using the i915 drivers.

I have not done any experiments or benchmarking. It does seem faster than my old T61.

73 Eric

Eric,

Have you done any further testing?  I am looking at ordering this particular laptop with the HD+ display.  I would like to hear from someone who has this working.

Thanks,
Joel

---

### Post by vab3 on 2012-07-15
Thanks for posting your experiences.  I'm wondering if anyone has tested the T530 with the nVidia graphics turned off in the BIOS. Is that possible, and how well does the system work with just the Intel HD 4000 graphics?  

Does unity 3D look nice? Can you watch the occasional YouTube or Netflix video?  What happens if you run a second, external monitor?

---

### Post by david on 2012-08-20
> **vab3 said:**
> Thanks for posting your experiences.  I'm wondering if anyone has tested the T530 with the nVidia graphics turned off in the BIOS. Is that possible, and how well does the system work with just the Intel HD 4000 graphics?  

Does unity 3D look nice? Can you watch the occasional YouTube or Netflix video?  What happens if you run a second, external monitor?

Hi, I turned off the nvidia graphics in my bios (using "integrated" graphics) and it works flawlessly. Intel integrated graphics are imo the best fit for regular use in ubuntu, I have no problem with video or 3D effects (although I primarily use gnome 3). The nvidia card is really only needed for high end games. The intel card is good enough for a lot of games though (I play minecraft for instance). 

Haven't tried external monitor yet, but my guess is that it should work unnless the nvidia card does something fishy I've had other lenovo laptops with integrated graphics and both display port and vga out works fine. Actually better than nvidia cards since they support xRandr.

My installation of Ubuntu went fine, but it used the noveau driver and before I changed to integrated graphics in the bios I had one or two crashes a day. Proprietary driver would probably fix that, but I only need integrated graphics for work. 

Ive been meaning to try out [http://bumblebee-project.org/](http://bumblebee-project.org/) to get both integrated and nvidia to work, but I haven't had time.

---

### Post by Aybara on 2012-09-12
It runs well on my T530. The only problem I have is that it won't boot with Discrete Graphics (just say "no video mode" or something like that forever.), and I suspect that with only the Integrated Graphics I can't make the minidisplayport work.

---

### Post by vab3 on 2012-09-12
Try installing the nVidia (nvidia-current) drivers from the Ubuntu Software Center, then change to discrete graphics in the BIOS.

> **Aybara said:**
> It runs well on my T530. The only problem I have is that it won't boot with Discrete Graphics (just say "no video mode" or something like that forever.), and I suspect that with only the Integrated Graphics I can't make the minidisplayport work.

---

### Post by pogopuschel on 2012-09-12
Nvidia-current will refuse to install if laptop is not set to discrete or switchable graphics.
If it refuses booting/starting X with discrete graphics, try the boot option
"nomodeset"...

---

### Post by Aybara on 2012-09-13
For me nvidia-current installed fine while on integrated graphics, and afterwards discrete graphics and minidisplayport works fine. Thanks.

Now I just gotta figure out how to get clamshell-mode working again. It broke when I installed the nvidia driver.

Edit: it was actually just in xmonad it broke, so disregard that comment.

---

