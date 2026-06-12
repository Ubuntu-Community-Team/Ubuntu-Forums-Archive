---
title: "Getting Adaptec HW Raid to work in 9.10"
date: 2009-12-28
forum: Hardware
---

### Post by benbrink on 2009-12-28
[FONT=Arial][SIZE=2]I am a relative newbie to linux in general---couple of years as a user on a laptop with nothing fancy--and an absolute novice to Ubuntu.

I have a server with an adaptec h/w raid. I cannot access the raid in linux (either SUSE or Ubuntu) but could when it was set up in windows 2000. I have checked the compatibility of the hardware and installed the following:
[/SIZE][/FONT][FONT=Arial][SIZE=2]**aac** - Adaptec AdvancedRAID Controller driver

The Ubuntu documentation now tells me to do the following:

  To compile this driver into the kernel, place the following lines in your
     kernel configuration file:

           **device** **pci**
           **device** **aac**
           **device** **aacp**

           To compile in debugging code:
           **options** **AAC_DEBUG=N**

     Alternatively, to load the driver as a module at boot time, place the
     following line in [loader.conf]("http://manpages.ubuntu.com/manpages/karmic/man5/loader.conf.5.html")(5):

           aac_load="YES"

I thought I would try the alternative solution first, but I cannot find the file
loader.conf anywhere. 

Where is it and is it really called loader.conf?












[/SIZE][/FONT]

---

