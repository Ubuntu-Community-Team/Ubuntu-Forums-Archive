---
title: "Splashy problem; video modes"
date: 2008-11-24
forum: General Help
---

### Post by Sirron on 2008-11-24
I have an Nvidia GTX 260 with the proprietary driver installed.

I want Splashy to work at my monitor's native resolution ideally, but seeing as my monitor's native resolution is 1680x1050, I expect that's not possible.

At the very least, I'd like it to be 1024x768, but unfortunately when I set /boot/grub/menu.lst to the mode I want, when grub starts ubuntu the Nvidia driver says it's an incompatible video mode, and quotes it wrong.

If I press enter, it then offers me a list of modes. If I type the number of the mode I want, it works fine, splashy uses that mode and all is well.

The modes all appear oddly though, rather than three numbers they have letters like hex... I expect it IS hex but I don't know where that leaves me.

I tried setting grub to use one of the modes offered by the error screen, like so:

```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=306e681d-f6a3-4c3c-84d2-7dab09894496 ro quiet **vga=33E** splash 
```

But it STILL wouldn't have it, and again, quoted it wrong.

So what exotic numbering system does Nvidia use for video modes?!

Thanks in advance

---

