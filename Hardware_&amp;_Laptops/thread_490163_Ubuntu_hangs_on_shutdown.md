---
title: "Ubuntu hangs on shutdown"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by bigpilot on 2007-07-02
Hi,

My Kubuntu machine works pretty much flawlessly but it won't shut down properly. I'm amazed that Ubuntu isn't able to detect the power management interface stuff flawlessly, I though that most distro's had this licked. 

Anyway when I shut down Kubuntu it hangs showing the Kubuntu logo with the progress bar. 

What can I do to remedy this situation?

---

### Post by Austin_KW on 2007-07-02
Try removing the "splash" from the boot options, this fixes the problem on on of my kubuntu PCs.

Alternatively try shutting down from the command line with "sudo shutdown -h now", some people report that this works.

---

### Post by bigpilot on 2007-07-04
But that's not really a solution is it? Why does it hang? How can I stop it hanging instead of having to stop it from the CLI?

---

### Post by Austin_KW on 2007-07-04
> **bigpilot said:**
> But that's not really a solution is it? Why does it hang? How can I stop it hanging instead of having to stop it from the CLI?

I dont know, mine hangs when attempting to show the boot "splash" on shutdown. If I remove splash by editing /boot/grub/menu.lst, then it does not hang.

---

### Post by bigpilot on 2007-09-01
I found out that it doesn't really hang but that it doesn't shut off the computer since it doesn't know how to handle the ACPI properly. Other Linux distros I've used (such as Puppy Linux) shut off the same computer perfectly. Why can't Ubuntu do this?

---

### Post by CyberCod on 2007-09-01
So far I've seen three different machines do this.  Its not an isolated thing.  I'm thinking perhaps that for hardware with unsupported or nonexistent power management, that they should include a Win98-esque "It's safe to turn me off now" message.  Have the command for it come AFTER the shutdown command, so that if the shutdown command fails, you get the message instead.

I dunno.  Something.

---

### Post by cpthk on 2008-06-11
I had ubuntu just 3 months older version installed without hang. But since today I reinstall my ubuntu with fresh installation and newest version, the problem start coming.

---

