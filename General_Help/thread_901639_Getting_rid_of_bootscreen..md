---
title: "Getting rid of bootscreen."
date: 2008-08-26
forum: General Help
---

### Post by OmnificienT on 2008-08-26
Hello,

I'd like to see what Kubi is doing when I boot it. Me thinking to be clever changed:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```
(In /boot/grub/menu.lst, with root priveleges.)

To:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
## defoptions=quiet splash

```

This didn't help, so I tried:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5

```

This didn't seem to make any difference either. What is my mistake?

Thank You,

OmnificienT

---

### Post by jigsaws on 2008-08-26
I think you're looking wrong place. Check options at "kernel" line.

---

### Post by silkstone on 2008-08-26
All the lines beginning with # (or ##) are comments - they aren't part of the instruction set. You need to scroll right down to the lines without comments.

If you remove the word 'quiet' from the appropriate line, it should show you everything during boot. I would recommend backing up menu.lst before making any changes.

---

### Post by OmnificienT on 2008-08-27
Thanks it worked. Is this also possible for debooting?

---

