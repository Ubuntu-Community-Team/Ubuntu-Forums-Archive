---
title: "Intrepid on V5535"
date: 2008-11-01
forum: Hardware
---

### Post by tonyalbers on 2008-11-01
Hi all,

I've had this Fujitsu Siemens laptop for quite a while now, and I've tried different distros on it. OpenSuSE kinda works, but I don't really like it.
So, I've installed Intrepid on it. The install went fine, but after installing, it won't boot.
I get the GRUB starup, and can get the menu, but after that ir just sits there with a blinking underscore on the top left corner of the screen. I've tried disabling ACPI and APIC, but no change.

Any ideas? It works fine off the live-cd.

TIA

/tony

---

### Post by tonyalbers on 2008-11-01
No ideas?

/tony

---

### Post by prshah on 2008-11-01
> **tonyalbers said:**
> The install went fine, but after installing, it won't boot.
I get the GRUB starup, and can get the menu, but after that ir just sits there with a blinking underscore on the top left corner of the screen.

Try giving either or all of the below kernel options (similar to when you've tried to disable ACPI / APIC):
a) vga=771 -OR- vga=ask
b) nosplash

Post back if you need more detailed instructions.

---

### Post by tonyalbers on 2008-11-01
Thanks,

Tried a and b, and noacpi and noapic. Result was the same every time: after pressing b to boot, the system resets.

/tony

---

### Post by kmbasu on 2008-11-03
Hi Tony,

you can try booting into the recovery mode, and then repair the x-server. See if it helps.

I could not make the sis 2D drivers work for the new kubuntu (8.10), also wireless didn't work, so giving up. The graphics diver worked in 8.04, though, there is a helpful discussion in ubuntu forums. As you said, opensuse's resolution was close, but not perfect. And no luck with wireless either.

Right now I'm using dreamlinux, guided by this helpful article
[http://dreamlinuxforums.org/index.php?topic=1341.0](http://dreamlinuxforums.org/index.php?topic=1341.0)

---

### Post by kmbasu on 2008-11-03
P.S. if you want to use KDE4, you may try Mandriva 2009, this is the only distro where (almost) everything have worked out of the box.

---

### Post by tonyalbers on 2008-11-05
yeah, but it doesn't even get to booting.

---

### Post by tonyalbers on 2008-11-05
> **kmbasu said:**
> P.S. if you want to use KDE4, you may try Mandriva 2009, this is the only distro where (almost) everything have worked out of the box.

Roger that, will try.

Thanks

---

### Post by kmbasu on 2008-11-05
Right, I remember the kubuntu 8.10 release candidate liveCD had this problem, but the final version got past that. Are you using the same?

Anyway, as I said, I don't plan to change this mandriva 2009 that I'm using anytime soon, enough experimentation!

---

### Post by tonyalbers on 2008-11-08
Just tried Mandriva 2009, after install it doesn't even get to GRUB, it just resets. Got two of these machines, same problem so it's probably not a broken machine I think.

Any other ideas? I really, seriously hate vista.

OpenSuSE works -sort of, only vesa graphics and no wifi. But I stopped using SuSE after Novell put their hands on it.

/tony

---

### Post by kmbasu on 2008-11-09
This is strange. Are you trying the 2009 One edition? I downloaded from here:
[http://www.mandriva.com/en/download](http://www.mandriva.com/en/download) 
The 'Free' version may have problem due to proprietary drivers etc, I'm not sure. Did your liveCD work?

As this is Ubuntu forum, may be we should discontinue the discussion here, you can ask in the Mandriva forum with details of your problem. I really had no such experience as you're mentioning in my V5535.

---

### Post by PaulHuygen on 2008-11-12
> **tonyalbers said:**
> Hi all,

I've had this Fujitsu Siemens laptop for quite a while now, and I've tried different distros on it. OpenSuSE kinda works, but I don't really like it.
So, I've installed Intrepid on it. The install went fine, but after installing, it won't boot.
I get the GRUB starup, and can get the menu, but after that ir just sits there with a blinking underscore on the top left corner of the screen. I've tried disabling ACPI and APIC, but no change.

Any ideas? It works fine off the live-cd.



I run Ubuntu Hardy (v.8.04) on a V5535. Although there were problems to be solved (resolution of the screen, network cards) Ubuntu ran well from the beginning. So, maybe you can give Hardy a try.

Paul

---

