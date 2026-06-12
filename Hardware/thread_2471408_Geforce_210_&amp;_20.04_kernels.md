---
title: "Geforce 210 &amp; 20.04 kernels"
date: 2022-01-29
forum: Hardware
---

### Post by valentin-kuzmin on 2022-01-29
neuavea driver for Geforce 210 does not work perfect: after some windows number it suspends the graphics.
The package installer does not install the Nvidia-340.108 driver complaining about something. And the
result: the system hangs at the boot on the first graphics.
If you try to install the driver from the Nvidia's script, it complains about an incompatibility with the kernel,
and the system is broken.
Is there a more or less simple way for usual user to use Geforce 210 in the 20.04 as well as it is in the 16.04?

---

### Post by Bashing-om on 2022-01-29
valentin-kuzmin; Hello -

What kernel are you on ?
As the 5.4 kernel is the last "mainline" to be supported:
see: [http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)
To know your kernel version run terminal command:
```

uname -r

```
There maybe support within our trusted PPA.
See: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
As seems that this PPA has support for the later kernel versions as provided by 20.04's HardWare Enablement (HWE) stack.

If we are to proceed here - will require confirmation that your system is cleaned up from all prior attempts to install the proprietary driver.
Is no big deal :)

Show us then: - Between code tags - the outputs of terminal commands:
```

dpkg -l | grep -i nvidia
sudo find / -name "NVIDIA-Linux-*"

```

[INDENT][INDENT]see what can be done
[/INDENT][/INDENT]

---

### Post by valentin-kuzmin on 2022-01-30
> **Bashing-om said:**
> valentin-kuzmin;

What kernel are you on ?

Thanks for the prompt answer.
The kernel is 5.13.0-27-generic.
Just now, a few minutes ago, after a few days of discussions on the Ubuntu-Russian forum I've got a solution. 
After checks I put it here.
At the moment I have
[IMG]https://i.ibb.co/8r728pV/w.jpg[/IMG]
[B]The solution
[/B]
My[B] case

[/B][I]sudo add-apt-repository ppa:kelebek333/nvidia-legacy
sudo apt-get update
[/I][I]sudo apt install nvidia-340
[/I]
[B]Other experience

[/B]*sudo add-apt-repository ppa:kelebek333/nvidia-legacy && sudo apt install xorg-modulepath-fix*

Good luck to owners of Geforce 210 & people needed the Nvidia-340 driver

---

### Post by Bashing-om on 2022-01-30
valentin-kuzmin' Great :D

Is good that you have a solution - 
Please provide for others this solution in this thread.

If this matter is now concluded >>
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]up up and away
[/INDENT]

---

