---
title: "Screen Flickering (At the start I am getting invalid video mode spec)"
date: 2018-02-24
forum: Hardware
---

### Post by yashkhandelwal on 2018-02-24
I have just upgraded to 17.10 and when I suspend the laptop and open the lid up screen flickers.Apart from it often happen my laptop shut down if I move the laptop.What to do?

---

### Post by DuckHook on 2018-02-24
Welcome to the forums, yashkhandelwal.

[list=1]
[*]> **yashkhandelwal said:**
> At the start I am getting invalid video mode specWhat do you mean by this? At GRUB? At login? What is the exact message?
[*]Provide your complete HW specs and the flavour you are using.
[*]Is this a new install or did you upgrade from Zesty?
[*]Post back to this thread the output from: ```
sudo lspci -vk | grep -iA20 vga
``````
cat /etc/default/grub
``````
echo $XDG_SESSION_TYPE
``````
xrandr
```
[*]Try running X instead of Wayland or vice versa.
[*]Try a LiveUSB of Xenial (16.04). What is the result?
[/list]

---

