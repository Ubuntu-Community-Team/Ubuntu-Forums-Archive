---
title: "Dell XPS 8300 - Compatible with Ubuntu?"
date: 2011-08-10
forum: Hardware
---

### Post by creepytennis on 2011-08-10
Hi, 

I've been offered a Dell 'XPS 8300' desktop at work. I need to know if it will work with Ubuntu. The machine is not let listed at the "Ubuntu Certified Hardware" site, and Dell do not give very much information about the specific hardware in the box:

[http://configure.euro.dell.com/dellstore/config.aspx?oc=d00x8301&c=uk&l=en&s=dhs&cs=ukdhs1&model_id=xps-8300](http://configure.euro.dell.com/dellstore/config.aspx?oc=d00x8301&c=uk&l=en&s=dhs&cs=ukdhs1&model_id=xps-8300) 

All I've got to go on is very vague: 

Intel® Core™ i3-2100 Processor (3.10GHz, 3MB) 
Graphics : Integrated Intel® HD 2000 
NVIDIA® GeForce GT 530 1GB DDR3 Graphics Card 
Sound : Integrated 7.1 with THX® TruStudio 

- So, Has anyone had any success installing Ubuntu on an 'XPS 8300' system?
- Could anyone suggest some obvious potential problems with this system?
- Does anyone know where I could find more information about the exact hardware? Does anyone know what the hardware really is? 

Thanks loads for any help! 

Jamie

---

### Post by Basher101 on 2011-08-10
You could make yourself a bootable USB and try it. Otherwise i dunno if it works

---

### Post by creepytennis on 2011-08-10
Thanks. I should have said: I don't have access to the machine. I need to decide whether to order it. If I had access, yep, I'd just try it! :-)

---

### Post by imbjr on 2011-09-04
> **creepytennis said:**
> Thanks. I should have said: I don't have access to the machine. I need to decide whether to order it. If I had access, yep, I'd just try it! :-)

This:

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19393751.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19393751.aspx)

suggests it is OK. I'm looking at purchasing one myself and found your thread.

---

### Post by imbjr on 2011-09-11
> **imbjr said:**
> This:

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19393751.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19393751.aspx)

suggests it is OK. I'm looking at purchasing one myself and found your thread.

Well, I'm running Natty-64-bit on a Dell XPS 8300 now, but there was an issue with the AMD Radeon HD 6670 card, whereby I'd just get a purple screen to look at instead of being able to log in. That happened with the recovery mode too.

The solution: download AMD's driver for the card and install it via chroot via live CD, boot into the OS and then install the driver that the OS then suggests for install. I'm getting insane fps with Minecraft now.

---

