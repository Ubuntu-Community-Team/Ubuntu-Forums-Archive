---
title: "Thinking of upgrading MoBo/CPU. How do I ensure a smooth transition?"
date: 2013-05-27
forum: Hardware
---

### Post by Mugsy323 on 2013-05-27
I currently have an older AMD Phenom II based setup that is configured just the way I like it. Now I'm looking to upgrade and I'm eying an *Intel* based setup.

Will Ubu automatically detect and reconfigure itself when I startup or must I reinstall?

When I was using Windows, an upgrade like this could be done simply by inserting the original Install disc and doing an "overwrite reinstall" of the OS. The installer would automatically detect and install the necessary files. But I've never done an upgrade like this using Ubu, and the last thing I want is to find out I can't switch platforms w/o reformatting.

Any help is appreciated. Thx.

---

### Post by ahallubuntu on 2013-05-27
~

---

### Post by Mugsy323 on 2013-05-27
> **ahallubuntu said:**
> I'm guessing it will work fine.  I've never switched architectures like you are doing, but I've moved drives between different machines many times rarely with any issue.  If you have some sort of custom video driver, you might remove that first before moving to the other machine.

Make sure the new motherboard chipset is well supported by the kernel you are using.

Remove the file /etc/udev/rules.d/70-persistent-net.rules if you want your default ethernet device to go back to eth0 when you move to the new hardware.  (The file gets regenerated at next boot with fresh values.)
Thanks for the reply. You gave me an idea. I have a laptop with an Intel processor. I'll try hooking my drive up to it first to see what happens. (Any suggestions on the best way to backup my boot drive first?)

Also, thanks on the Ethernet info. The new MoBo uses a different Ethernet controller.

---

### Post by ahallubuntu on 2013-05-27
> **Mugsy323 said:**
> Thanks for the reply. You gave me an idea. I have a laptop with an Intel processor. I'll try hooking my drive up to it first to see what happens. (Any suggestions on the best way to backup my boot drive first?)

Why do you need to backup your boot drive?  Not that you shouldn't back up your drive anyway, but simply booting another OS from an external drive shouldn't put your boot drive into any danger.

> Also, thanks on the Ethernet info. The new MoBo uses a different Ethernet controller.

Actually, it could be exactly the same ethernet controller and you'd want to do exactly the same thing.  The MAC address would still be different, so unless you blow away the udev rules file, it will bump you up to eth1.

---

### Post by Mugsy323 on 2013-05-28
> **ahallubuntu said:**
> Why do you need to backup your boot drive?  Not that you shouldn't back up your drive anyway, but simply booting another OS from an external drive shouldn't put your boot drive into any danger.

Actually, it could be exactly the same ethernet controller and you'd want to do exactly the same thing.  The MAC address would still be different, so unless you blow away the udev rules file, it will bump you up to eth1.
Thanks for the reply.

I just tried it on my laptop and it worked perfectly w/o changing a thing (try that with Windows). I was concerned about backing the drive up in case it was "reconfigured" in some way by putting it on new hardware, but I guess that's only something *Windows* users need to concern themselves with. :)

I didn't delete the Ethernet file just for the test but will before I make the platform switch. Thx.

---

### Post by ahallubuntu on 2013-05-28
You can delete that udev file at any time before or after you move the drive.  The only drawback of not doing so is that your network devices are remembered from the old system so your network card becomes "eth1" (or probably now "eth2") instead of eth0.  Usually this doesn't cause any issues, but it might throw you not to see "eth0" anymore when looking at network stuff.  If you have a static IP set for eth0, though, then you'd want to make the fix.

---

