---
title: "Ubuntu 18.04 and IR remote control: How is this configured?"
date: 2021-08-17
forum: Hardware
---

### Post by kzembower on 2021-08-17
Hello, all.

I'm trying to set up my MythTV box on a Raspberry Pi 4 with a Vista MCE controller, model VRC-1100. For testing purposes, I connected the receiver via USB to my desktop Ubuntu 18.,04 system, and was surprised that many, but not all, of the keys on the remote do something. For instance, the POWER key on the remote seems to put my system into suspend.

I'm trying to learn how this is configured and what it's doing. I think that I've never installed LIRC on this system, but I could be mistaken and have installed it when I first bought this remote, about 4 years ago. I tired to purge my system of all lirc-related files and packages, but the remote control still seems to work. There's no running processes with 'ir' in their name that seem relevant. There's no kernel mods that seem relevant either. So, what's controlling this action?

I'm also confused by the current state of IR communications. Something I read said that IR control is now built into the kernel (I'm currently running 4.15.0-153-lowlatency). Other posts I read is that LIRC shouldn't be used, and has been replace by another package, but I don't think I have that package.

Can anyone help me learn more about how this IR RC is interacting with my system?

Thanks so much for your thoughts and suggestions.

-Kevin

---

