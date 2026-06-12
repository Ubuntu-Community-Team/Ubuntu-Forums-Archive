---
title: "HP 2740p - rotating screen and use screen buttons issues"
date: 2010-10-04
forum: Hardware
---

### Post by scholarmed on 2010-10-04
Dear All,

I got a new HP 2740p Elitebook. It is a convertible notebook with multi touch screen.

My question is the following: After rotating the screen e.g. for 90°, the mouse is 'screwed' and I can't work properly. It seems that the mouse stays in the old position.

I already looked out for some help, but I think I don't understand most of the things not correctly, because it is still not working! ;)

Can somebody provide some help? The keys on the screen aren't working as well. Might there be a possibility to use them as well?

I'm a bit clueless what information (hardware / software) needs to be shared. For now I'm working on a Ubuntu 10.10 system. lshw gives the following output for video

```
  description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:90000000-903fffff memory:80000000-8fffffff ioport:5058(size=8)

```Thanks for every help in advanced, it is really appreciated!

------------------
Ubuntu 10.10

---

### Post by scholarmed on 2010-10-09
hmm, nobody?

---

### Post by scholarmed on 2010-10-13
The problem solved 'almost' by itself.

The ppa of Tom Jaeger helped me out. It works after a restart out of the box.

You may find the ppa here: [https://launchpad.net/~thjaeger/+archive/tabletpc](https://launchpad.net/~thjaeger/+archive/tabletpc)

Steps:

1. Install the ppa with:
```
sudo add-apt-repository ppa:thjaeger/tabletpc
```

2. update repository:
```
sudp apt-get update
```

3. Install script
```
sudo apt-get install wacomrotate
```

4. Reboot or Logout

The script loads automatically and changes the input automatically.

Hope that helps somebody.

Further reading for this topic can be found here:

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/217182](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/217182)

---

### Post by Getmarken on 2012-02-18
Hello! I have tried and partly succeded to get my screen rotating by the help you gave in this Thread. But there is a very big problem: The touch will not synk. I have a HP 2740p too. Every time I rotate the screen the touchpoint meet my finger in the center. when I move my finger the pointer goes in another direction e.g if i touch in the left down corner the pointer is in upper right. If I touch in upper right corner the pointer will be in down left.
Maybe the soulotion is in the descriptions but I can not find out how to do. Please help. This laptop is new for me and I don't want to use Windows again.

---

### Post by scholarmed on 2012-02-28
> **Getmarken said:**
> Hello! I have tried and partly succeded to get  my screen rotating by the help you gave in this Thread. But there is a  very big problem: The touch will not synk. I have a HP 2740p too. Every  time I rotate the screen the touchpoint meet my finger in the center.  when I move my finger the pointer goes in another direction e.g if i  touch in the left down corner the pointer is in upper right. If I touch  in upper right corner the pointer will be in down left.
Maybe the soulotion is in the descriptions but I can not find out how to  do. Please help. This laptop is new for me and I don't want to use  Windows again.

Hey!

Yeah, I have exactly the same problem. It seems there is a bug in the wacom driver. But it shall be fixed in Precise Pangolin 12.04.

Iit can also be fixed beforehand, but it will probably give you a more unstable feeling. So I would suggest to wait.

You can find the details over here:
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647)

Sorry for the long waiting! 
Cheers

---

