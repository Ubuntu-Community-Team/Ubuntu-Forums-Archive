---
title: "What motherboard can I use for Ubunu 12.04?"
date: 2016-05-03
forum: Hardware
---

### Post by dmtsuser on 2016-05-03
Hi,

I want to set up a Ubuntu 12.04 system for MRI analyses. I will need 12.04, because some of the analysis software is not properly working wit later Ubuntu versions. 
Can anybody recommend a motherboard for such a system with an Intel Core i7-6700K? Maybe an Gigabyte GA-H170-HD3?

Any help is greatly appreciated! 

togtogtog

---

### Post by mörgæs on 2016-05-03
I think you will be better off by trying to get the software to work with a newer release of Ubuntu.
What happens if you try installing in 14.04 or 16.04?

---

### Post by jeremy31 on 2016-05-03
> **mörgæs said:**
> I think you will be better off by trying to get the software to work with a newer release of Ubuntu.
What happens if you try installing in 14.04 or 16.04?
+1 on that as 12.04 will only be supported for another year +/-

Do you know the exact cause of needing 12.04?

---

### Post by weatherman2 on 2016-05-03
There is nothing wrong with leaving 12.04 on the machine for a long time if it is needed only for a certain piece of software and the machine has limited exposure to the internet.  Just don't expect updates anymore.

Another option would be to install 12.04 in a virtual machine while hosting in a newer version of Ubuntu.  Then you can use any host hardware you want and not worry about the motherboard, unless the software itself is hardware-dependent.

---

### Post by dmtsuser on 2016-05-04
Thank you all for your comments!
Basically, the problem is with SGE/Qmon that I will need for FSL ([http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslSge](http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslSge)) - it's working well with 12.04, but we and others had problems setting it up with 14.04 and get it running with FSL...
Would a virtual machine support SGE?

---

### Post by weatherman2 on 2016-05-04
I don't know what SGE/Qmon is, but unless it relies on specific hardware, it should work fine.  Even if there is some hardware dependency, some tinkering with the virtual machine (I use Virtualbox) can still expose the hardware you may need to get the software to run.

I suggest simply trying it.  I'm not sure if you can simply port your existing 12.04 install to a virtual machine - probably possible but I've never tried it.  It may be easier to re-install.  Still, once you do that, your virtual machine is quite portable to other hosts.  I have couple of Virtualbox installs of Windows that I have moved to different Ubuntu machines as needed, without needing a complete re-install.

---

### Post by ZoiaGuyver on 2016-05-05
I would probably go for something based around the C236/C232 Intel chipsets something like the [GA-X150-Plus-WS]("http://www.gigabyte.com/products/product-page.aspx?pid=5704#ov")

Thats assuming that SGE/Qmon (Sun Grid Engine) is required. The C2xx chipsets are imo more reliable than the H170/Z170 as they are more Workstation/Server classed products. You also have the ability to upgrade to a Xeon if needed for the extra punch they can pack in multi-threading workloads.

---

### Post by mörgæs on 2016-05-05
I don't know what Sun / Son of Grid Engine is but this list seems well updated:
[http://arc.liv.ac.uk/downloads/SGE/releases/](http://arc.liv.ac.uk/downloads/SGE/releases/)

---

