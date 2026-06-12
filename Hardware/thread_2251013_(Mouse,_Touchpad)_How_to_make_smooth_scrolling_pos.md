---
title: "(Mouse, Touchpad) How to make smooth scrolling possible?"
date: 2014-11-01
forum: Hardware
---

### Post by henning4 on 2014-11-01
Hello ubuntu friends,

since i've been using ubuntu on my laptop i am thinking that smooth scrolling with a touchpad (or the third mousebutton) would be a big advantage.
Today I had a look at the synaptics touchpad driver to check how it is implemented and if it could be customized.
I found out that two finger scrolling is made possible by posting a mouse-button event using the **[COLOR=#000000]xf86PostButtonEvent()[/COLOR]**[COLOR=#000000] function from [/COLOR][COLOR=#000000]<xf86.h>.

I am wondering if there is an event to trigger or anything else to call that performs scrolling in a smooth way?
Any help, references or people/places to contact would be much appreciated.

Kind regards,
Henning[/COLOR]

---

