---
title: "Dell MPBIOS problems"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Gray0005 on 2009-08-24
[FONT=Arial][SIZE=2]I am trying to get linux to run on an old Dell. I have installed Xubuntu 9.04 from two separate disks and I have gotten the same exact problem two times. So, I’m guessing that it is not the disks. I have successfully installed Xubuntu into the hard disk and the computer knows to boot to xubuntu when I start up. Here are the prompts I see. (The plus signs signify new lines)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Starting up…[/SIZE][/FONT]
[FONT=Arial][SIZE=2][0.972002]… MP-BIOS bug: 8254 timer not connected to IO-APIC ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Loading, please wait…++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Gave up waiting for root device. Common problems: ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Boot args (cat/proc/cmd line) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Check rootdelay =(did the system wait long en enough?) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Check root= (did the system wait for the right device?) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Missing modules (cat /proc/ modules; Is /dev) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]ALERT! /dev/disk/by-uuid/175fd1df-b7a7-4a00-a984-8fbeb1fe88 does not exist. Dr opping to a shell![/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]BusyBox v1.10.2 (Ubuntu 1:1.10.2ununtu7) built-in shell (ash) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Enter help for a list of commands ++++[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2](initramfs) _ ++++[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]From here it stays with a flashing curser.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]So.. Apparently there is a way to edit the boot sequence so that apic is disabled and apparently this has fixed the problem for other people. If anyone knows how to do this, please walk me through the process. I am not the best with computers, so if you could write your response as if you're communicating with a six year old that would be appreciated. Thanks, linux is an attractive idea to me because of it ethical and social appeal. If anyone could help me become a part of the community it would be appreciated! -Chris[/SIZE][/FONT]

---

