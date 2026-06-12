---
title: "Mouse Scroll rate"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by brainz on 2005-08-25
How to increase the mouse scroll wheel  to do more lines? The option is not specified in Gnome mouse preferences?

I also tried xorg.conf looking in xorg.conf but there was no option at all.

---

### Post by s_p_a_r_k_y on 2005-08-25
might be an application to application thing
in firefox for example, go to about:config
filter by mousewheel
and you will find some settings. I set my default mousewheel.withnokey.numlines to 10
and withcontrolkey.numlines to 20

Google for how to do it with other applications

---

### Post by brainz on 2005-08-25
[QUOTE=s_p_a_r_k_y]might be an application to application thing
in firefox for example, go to about:config
filter by mousewheel
and you will find some settings. I set my default mousewheel.withnokey.numlines to 10
and withcontrolkey.numlines to 20

Google for how to do it with other applications[/QUOTE]

Is there any way to set it for all gtk-apps?

---

### Post by s_p_a_r_k_y on 2005-08-25
my searching google did not show anything useful. Perhaps you can checkout the gnome mailing lists or check them out on irc, irc.gnome.org #gnome i think and ask around

---

### Post by brainz on 2005-08-25
[QUOTE=s_p_a_r_k_y]might be an application to application thing
in firefox for example, go to about:config
filter by mousewheel
and you will find some settings. I set my default mousewheel.withnokey.numlines to 10
and withcontrolkey.numlines to 20

Google for how to do it with other applications[/QUOTE]


For convenience, I will summarize the process for future users:

1) type about:config in Firefox's address bar
2) find the preference named "mousewheel.withnokey.numlines"
3) enter an integer (this is the number of lines scrolled per notch on the mouse wheel)
4) find the preference named "mousewheel.withnokey.sysnumlines"
5) change the value to "false" (this tells firefox not to use the system's setting for scroll-rate, which usually defaults to 3).

To make Firefox scroll at the same rate as IE, enter a value of 7 for "mousewheel.withnokey.numlines

---

