---
title: "Ubuntu Thinks 2nd Monitor is 32&quot; when it's 19&quot;?"
date: 2012-05-04
forum: Hardware
---

### Post by Jamie_Edwards on 2012-05-04
Hi guys,

This is sort of two problems ( which I think are related and are causing this problem ) in one.

I bought an VTX ATi Radeon HD 5450 graphics card to enable me to use a dual monitor setup ( one 15" VGA monitor and one 19" HDMI monitor ) running with the Catalyst Control Centre driver ( official ). When I was still using 11.04 my HDMI monitor stopped working and I never got to the bottom of it.

But when I upgraded to 12.04 both monitors started working, so I decided to re-install the official driver to once again find my HDMI not working. After a fresh install I started searching and found that Ubuntu has the following problems.

In System Settings > Monitor it says that I have a 15" Philips VGA Monitor ( No problems here ). But for some strange reason, my HDMI monitor comes up with:

"CVT 32" TV"

WTF? My HDMI monitor is a 19" HDTV by Technika.

So I tried looking for a solution as to why Ubuntu thinks my monitor is a 32" and after a while I found and run the "lshw -c video" command which comes up with the following:

 *-display               
       description: VGA compatible controller
       product: RS780L [Radeon HD 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff
  *-display
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5430 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:d0000000-dfffffff memory:feae0000-feafffff ioport:d000(size=256) memory:feac0000-feadffff

The first one I guess is my on board graphics, as for the second one it says "product: Manhattan [Mobility Radeon HD 5430 Series]"
Now I am very sure I have a VTX Radeon HD 5450 I found out that the graphics card Ubuntu thinks the right one is actually for laptops ( I use a desktop pc ).

Any idea's?

Thanks.

Jamie.

PS. Sorry if this post is a tad long :L but I hope you guys can help.

---

### Post by papibe on 2012-05-04
Hi Jamie_Edwards.

I'm no expert on AMD/ATI cards, but from my experiences with Nvidia, it looks like both graphics are activated. That it not always desirable, so if I were you, I would go to BIOS and try to set the ATI card as the default graphics.

If you are trying to use both at the same time (a little more complicated matter) take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=ATI").

Just some thoughts.
Regards.

---

### Post by Jamie_Edwards on 2012-05-04
> **papibe said:**
> Hi Jamie_Edwards.

I'm no expert on AMD/ATI cards, but from my experiences with Nvidia, it looks like both graphics are activated. That it not always desirable, so if I were you, I would go to BIOS and try to set the ATI card as the default graphics.

If you are trying to use both at the same time (a little more complicated matter) take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=ATI").

Just some thoughts.
Regards.

Thanks, I'm using only the external graphics card, but I shall have a go at changing the BIOS and get back to you on the outcome

---

### Post by Jamie_Edwards on 2012-05-04
TBH I don't know how to disable the integrated graphics :L

I have the Asus M4A78LT-M LE motherboard. if anyone knows how, and could give me a step-by-step, that would be great.

---

### Post by Jamie_Edwards on 2012-05-05
Apparently you can't "disable" the onboard graphics, but instead change the order of which the system looks for a graphics card, and at the moment I have this order:

GFX0-GPP-IGFX-PCI

Where GFX0 is the primary video controller on a PCIe x16 slot ( which is where my dedicated card is ) and IGFX is the integrated graphics is. So I shouldn't technically be getting this problem?

---

### Post by gordintoronto on 2012-05-05
Ubuntu doesn't care how big your display is, only its resolution. If the detected TV and the actual TV are both 1080 by 1920, the incorrect detection shouldn't matter at all.

What does Catalyst have to say?

---

### Post by Jamie_Edwards on 2012-05-07
> **gordintoronto said:**
> Ubuntu doesn't care how big your display is, only its resolution. If the detected TV and the actual TV are both 1080 by 1920, the incorrect detection shouldn't matter at all.

What does Catalyst have to say?

I don't have it installed as for some reason it either breaks the OS ( by giving me the boot screen and then hangs at that point ) or my HDMI monitor breaks and doesn't have anything outputted to it.

---

