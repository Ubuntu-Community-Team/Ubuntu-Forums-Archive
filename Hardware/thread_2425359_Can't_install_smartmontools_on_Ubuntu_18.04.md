---
title: "Can't install smartmontools on Ubuntu 18.04"
date: 2019-08-24
forum: Hardware
---

### Post by lrPrentice on 2019-08-24
Hello,

I'd like to check disc health on my newly installed Ubuntu 18.04 system. Google search tells me that I need to install smartmontools. So, I enter:

sudo apt install smartmontools

Looks like it's going to install, but then I get a static screen that says:

Postfix Configuration

This screen shows several options, but not a hint of how to select these options. I've searched every keyword I can think of but can't find an answer. So I'm stuck.

Can some kind soul tell me how to get past this roadblock?

Many thanks,

LRP

---

### Post by Bashing-om on 2019-08-24
lrPrentice; Hummm ....

My imagination does not extend to " Postfix Configuration" in this instance.

what results from terminal commands:
```

sudo apt update
sudo apt upgrade
apt list smartmontools

```

As we look beneath the covers.

[INDENT][INDENT]gots to be more to it than just that
[/INDENT][/INDENT]

---

### Post by CatKiller on 2019-08-25
> **lrPrentice said:**
> Looks like it's going to install, but then I get a static screen that says:

Postfix Configuration

This screen shows several options, but not a hint of how to select these options. I've searched every keyword I can think of but can't find an answer. So I'm stuck.

Postfix is an email server so that you can be emailed notifications of SMART warnings. Generally with those screens that come up with install scripts you use the cursor keys, tab, space, and enter to select things.

---

