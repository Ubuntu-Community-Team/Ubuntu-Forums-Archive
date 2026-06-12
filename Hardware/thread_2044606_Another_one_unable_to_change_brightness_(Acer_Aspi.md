---
title: "Another one unable to change brightness (Acer Aspire One D270)"
date: 2012-08-19
forum: Hardware
---

### Post by nosredna on 2012-08-19
I'm probably not the only one suffering from this problem, it seems to be pretty common for users to loose the feature of changing brightness in Lubuntu 12.04, and by changing brightness I mean by using the standard button combination (Fn + Left, Fn + Right or Fn + F9, Fn + F10 and so forth). Many has resolved this problem simply by putting some lines in **/etc/default/grub**. I've tried many of these, for instance: 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
```
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=video"
GRUB_CMDLINE_LINUX=""
```

But to my avail. Not that I really know what these lines do, except enabling brightness to be changed for some users, I'm pretty much a n00b you see. I'm of course able to change it through the terminal using ```
sudo setpci -s 00:02.0 F4.B=xx
```, but this already feels somewhat tiresome, I'm too used to the buttons. 

Intel recently released [this]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=21519") driver for my chip but I can't find any instructions for how to install it, I know this has solved the brightness problem for some, but in order for that to work for me I need to know how to get it going. I'm just sitting  here with a folder named "cdv-gfx-drivers-1.0.1_bee". Well well.

What about a work around? Like binding keys? I wrote this in the terminal ```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

``` and tried some combinations, Fn + Right & Fn + Left is two of those who do not get recognized, which is weird since Fn + Up and Fn + Down is, and the previous two is supposed to be just as standard, at least according to the brightness symbols upon them. :p Does that mean I can't bind anything to this button combination? And if I'm still able to bind, what commands are the correct ones?

Any guidance, my friends?

---

### Post by nosredna on 2012-08-20
I understand if someone doesn't want to approach this problem because it's so general and hard to see where to begin. But maybe someone instead could help me with this more concrete problem; installing the drivers that I described at the bottom of my post? Maybe that's the solution for me?

---

### Post by oxf on 2013-01-23
> **nosredna said:**
> I understand if someone doesn't want to approach this problem because it's so general and hard to see where to begin. But maybe someone instead could help me with this more concrete problem; installing the drivers that I described at the bottom of my post? Maybe that's the solution for me?

I too have just installed Lubuntu 12.04 LTS on my  Acer Aspire One and have the same problem.

I also have Ubuntu 12.04 on the same machine. When that is first installed the same issue occurs. However, once I installed the cedartrail driver which was available in "additional drivers" the problem resolved itself. The problem here is that there is no additional driver listed in Lubuntu option. 

So how do we get the additional driver for Lubuntu?

---

