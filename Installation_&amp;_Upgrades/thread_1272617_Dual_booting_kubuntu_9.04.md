---
title: "Dual booting kubuntu 9.04"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by m_w_a on 2009-09-22
I'm just beginning to install my first Linux distro so apologies for being a complete noob. I began the installation of Kubuntu 9.04 from my live cd, with the intention of dual booting with Windows. Based on what I've read I was expecting to be presented with the option of dual booting but when it came to partitioning the drive I had the option of partitioning the entire drive (close to 80gb) or selecting the partitions myself. When I chose to select the partitions myself I was presented with options that overwhelmed me. I have watched a few videos of installing Ubuntu and was expecting something similar to what I had seen, with a simple slider that allowed you change the ballance between Windows and Ubuntu. Is this simply not available when installing Kubuntu? 

On a side note, my computer is infected with rootkit and probably a couple other viruses that constantly cause Windows to freeze. I can only boot up Windows successfully in safe mode and as such I can't defragment the drive. How important is it to defrag before installing Kubuntu?

---

### Post by presence1960 on 2009-09-22
> **m_w_a said:**
> I'm just beginning to install my first Linux distro so apologies for being a complete noob. I began the installation of Kubuntu 9.04 from my live cd, with the intention of dual booting with Windows. Based on what I've read I was expecting to be presented with the option of dual booting but when it came to partitioning the drive I had the option of partitioning the entire drive (close to 80gb) or selecting the partitions myself. When I chose to select the partitions myself I was presented with options that overwhelmed me. I have watched a few videos of installing Ubuntu and was expecting something similar to what I had seen, with a simple slider that allowed you change the ballance between Windows and Ubuntu. Is this simply not available when installing Kubuntu? 

On a side note, my computer is infected with rootkit and probably a couple other viruses that constantly cause Windows to freeze. I can only boot up Windows successfully in safe mode and as such I can't defragment the drive. How important is it to defrag before installing Kubuntu?

It is very important to defrag windows at least once or twice because you are going to resize the windows partition to create space for Ubuntu. Windows has a bad habit of haphazardly throwing files all over it's partition. I would even disable system restore until after Ubuntu is installed.

I would suggest you fix your windows problem first if you are going to dual boot. If you don't want to use windows then select use entire disk option. Which brings me back to the first statement, if you want to dual boot then that means you intend on using windows. if that is true straighten out your windows install first or format your disk, reinstall windows, defrag windows (yes, even after an install as that is some of the worst fragmentation ever seen), then try installing Ubuntu.

---

### Post by m_w_a on 2009-09-22
You make a good point. I was only hanging on to Windows in the event that I needed to use a program that won't run in Linux but I have XP on another machine anyway so there isn't much point. I know I'll never go through the torture of trying to get rid of rootkit so I might as well just replace it. But just to clarify, if I tell the Kubuntu installation to use the entire disk, it doesn't matter if the drive has been defraged? And this may sound completely idiotic but if i do select "use entire disk" I'm not going to be left without any memory on the drive am I?

---

### Post by presence1960 on 2009-09-22
> **m_w_a said:**
> You make a good point. I was only hanging on to Windows in the event that I needed to use a program that won't run in Linux but I have XP on another machine anyway so there isn't much point. I know I'll never go through the torture of trying to get rid of rootkit so I might as well just replace it. But just to clarify, if I tell the Kubuntu installation to use the entire disk, it doesn't matter if the drive has been defraged? And this may sound completely idiotic but if i do select "use entire disk" I'm not going to be left without any memory on the drive am I?

If you select use entire disk the whole disk will be formatted to Ubuntu's filesystem which means Windows, rootkits & other nasties will be overwritten. The whole disk will use Ubuntu just like windows installed itself and used the whole disk.

---

