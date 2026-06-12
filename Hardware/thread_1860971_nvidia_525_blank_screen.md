---
title: "nvidia 525 blank screen"
date: 2011-10-15
forum: Hardware
---

### Post by pavankumarl73 on 2011-10-15
Hello all,
       I'm using dell xps with core i7 and nvidia 525 [ubuntu 11.10, 64 bit ], I installed nvidia using additional drivers and ran nvidia-xconfig command but after reboot I ended up in blank screen. If I don't enable graphics card my laptop runs increasingly hot. 
   
     Also I don't get battery backup in ubuntu. In windows I get nearly 4 hours but in ubuntu I hardly get 2 hours.

     Even in ideal conditions if I look system monitor I can see 2 to 4 CPUs showing 5% to 10% usage. What does this mean ? Is it related to nvidia or something else.

Please provide me your feedback about what needs to be done to rectify all these problems

---

### Post by Hanine on 2011-10-28
Does your System have Nvidia Optimus?

Otherwise, your laptop's configuration : does the system have an onboard graphics card (Intel HD 3000) + Nvidia GT 525M ?

IF so, then Ubuntu 11.10 is not yet compatible with Nvidia OptimusTechnology yet! 

TO solve the problem, check the bumblebee project.
You'd have to install Bumblebee that supports Nvidia Optimus.

Go to their website and follow instructions.

In case your system does not have Optimus then, installing Nvidia legacy drivers should be fine.

The black or blank screen you have means there is a conflict between the Intel HD 3000 drivers and the Nvidia GT525M drivers.

You can also (only in some configurations) disable the Nvidia Card on the Bios or apply this:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15#Optimus_.2BAC8_Graphics_cards](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15#Optimus_.2BAC8_Graphics_cards)

---

### Post by pavankumarl73 on 2011-10-29
Hi,
   Thank you, my problem solved

---

### Post by Hanine on 2011-11-01
> **pavankumarl73 said:**
> Hi,
   Thank you, my problem solved

Ok Great!
Could you tell us what you did so everybody could learn from your post please :)

---

### Post by pavankumarl73 on 2011-11-02
Hello everyone,
    I have dell xps with i7 core and nvidia 525.This is what I did to solve optimus problem. But yes there are few problems does exists.
  
 1. First install ironhide optimus solution. 
    
    ```
sudo apt-add-repository ppa:mj-casalogic/ironhide
    sudo apt-get update && sudo apt-get install ironhide
```

 2. If you have bumblebee solution pre-installed ironhide will remove it and will install ironhide as both conflict.

 3. Follow the on-screen instructions to install the solution

 4. To shutdown the nvidia gpu use the command 
     
    ```
sudo ironhide-disablecard
```

    To shutdown nvidia card at start-up use the command
    
    ```
sudo ironhide-disablecard-on-startup
```

    ( I'm on windows machine, so please do check the command by using TAB key, I hope it is clear what I meant )

 5. To enable nvidia card use the command
    
    ```
sudo ironhide-enablecard
```

 In my case I encountered problem when I tried to enable nvidia gpu( my nvidia gpu disables at start-up so I never tried to disable gpu after enabling it manually )
    
    ERROR : module nvidia cannot be found in /proc/modules
    Cannot enable nvidia.

  But this problem can be corrected by using proper configuration settings.

Problems still facing :
 
 1. Less battery backup
 2. 1500+ processor wake-ups even in ideal conditions (I could see CPU graph popping up every second upto 10% on at least 2 of the 8 graphs displayed in system monitor)

 I did a small search regarding processor wake-ups and installed "powertop" and set auto-turnoff for all the PCI devices but it didn't yield any significant improvement in wake-ups and battery backup.I even installed "jupiter" to improve battery backup but ended up empty handed. I believe root cause is still the OPTIMUS issue though I disabled nvidia gpu. 

I get 3+ hours battery backup with wireless on on windows but in ubuntu it hardly shows up 2hr 30min.

If anyone knows how to decrease the number of processor wake-ups please provide the solution here. And what is the average processor wake-ups I can expect? And how to improve my battery backup?

Thank you

---

