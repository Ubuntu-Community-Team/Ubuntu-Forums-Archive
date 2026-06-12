---
title: "QLogic Fibre Channel"
date: 2014-12-22
forum: Hardware
---

### Post by mrJTparadise on 2014-12-22
Hi everyone - new here.

First of all I'd like to state that I am new to fibre channel and qlogic so please bear with me.  I am going to explain my setup first and then the problem I am having.

[B]Setup/Environment

[/B][U]Computer A
[/U]Ubuntu 14.04.1 LTS with 3.13.11.8.141203scst kernel 64-bit
Four SSDs connected to a SATA controller
Fibre Channel PCI card with 2 ports ( do not know the specifics )

Is this computer referred to as the host?

[U]Computer B
[/U]Ubuntu 12.04.2 LTS with 3.2.0-40 generic kernel 64-bit
Fibre Channel PCI card with 2 ports ( do not know the specifics )

Is this computer referred to as the target?

**Problem**

I've went through the configuration of qlogic and built a new kernel so we can skip the explanation of the steps - I think?  The guide I used is listed here - [http://scst.sourceforge.net/qla2x00t-howto.html](http://scst.sourceforge.net/qla2x00t-howto.html)

On Computer A I have a script that generates a config file for scstadmin to load.  In short, it generates a config a file with the appropiate targets.  I have two targets that look like MAC Addresses (WWNs).

How does the host know the target?  Is the target the WWN of the fibre channel port on Comuter A or Computer B?  The reason I am asking is because I have a pair of TARGET in my config file with two different WWNs. This makes sense becuase I have two ports on the fibre channel card but in the config file only the raid1/3 is being recognized on Computer B when I do an 'lsscsi'.  If inside the TARGET parameter of the config file, is the WWN supposed to be that of Computer B or Computer A?  The reason I am asking is because I have a hunch that the first WWN that is for raid0 and raid2 does not exist or is incorrect.  

Below is my config file : 

 ```
 HANDLER vdisk_fileio { 
      DEVICE raid0 {      
         filename /xxx0/raidDiskImage0.img 
      } 
      DEVICE raid1 {      
         filename /xxx0/raidDiskImage1.img 
      } 
      DEVICE raid2 {      
         filename /xxx0/raidDiskImage2.img 
      } 
      DEVICE raid3 {      
         filename /xxx0/raidDiskImage3.img 
      } 
  }
  TARGET_DRIVER qla2x00t { 
    TARGET 21:00:00:e0:8b:88:81:2d { 
      HW_TARGET 
      enabled 1 
      rel_tgt_id 1 
             LUN 0 raid0 
             LUN 1 raid2 
    }
    TARGET 21:01:00:e0:8b:a8:81:2d { 
      HW_TARGET 
      enabled 1 
      rel_tgt_id 2 
             LUN 0 raid1 
             LUN 1 raid3 
    }
  }
  TARGET_DRIVER scst_local { 
    TARGET scst_local_tgt { 
       session_name scst_local_host 
    LUN 0 raid0
    LUN 1 raid1
    LUN 2 raid2
    LUN 3 raid3
    } 
  } 

```

Any input is much appreciated and I thank any of you for your time to read this.

-JT

---

### Post by mrJTparadise on 2014-12-22
Everything is setup correctly, I just needed to remove and add the qla2xxx module on the target machine.  May have something to do with a chicken/egg scenario.

Mark as solved/closed please.

---

