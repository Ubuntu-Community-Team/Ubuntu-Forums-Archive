---
title: "Synaptics touchpad driver: how to get a smoother scrolling?"
date: 2010-01-29
forum: Hardware
---

### Post by Cenoforums on 2010-01-29
Hi,

If you really think about this, it's a stupid behaviour. Touchpad scrolling is implemented in the synaptics driver by emulation mouse buttons 4 and 5, which in a usb mouse is the events the scroll wheel generates.

Now that I noticed this, it's incredibily annoying. Scrolling with the touchpad should exhibit the same behaviour as dragging the scroll bar up and down. Meaning that a distance made with the finger along the touchpad corresponds to a distance made in the scroll bar, as opposed to a distance made with the finger corresponding to a number of discrete button4/5 events.

Does any know if there is anyway to achieve this? A different driver, some hack?
I'm sure this is how it works in OSX, and I could bet it's how it works on windows although I haven't used it in so long I don't really remember.

---

