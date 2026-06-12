---
title: "Output Sound Keeps Changing Sink"
date: 2024-10-23
forum: Hardware
---

### Post by jbhardman2 on 2024-10-23
Long time arch linux desktop user. Just trying Ubuntu. Every time I restart, or after my laptop goes to sleep mode and I wake it up, my sound output changes. Sometimes I plugged in at my desk to a USB-C Hub and it will change to my USB microphone (which I don't have headphones plugged in to). When the laptop is not hooked up, it changes to the HDMI out port which is not plugged in.

The correct output is right there in the list, "Speaker". I change it to speaker and immediately sound comes from the laptop speakers.

Why does this constantly change all on it's own?

Ubuntu Desktop 24.10, Lenovo Thinkpad Carbon X1 Gen 9.

---

### Post by jbhardman2 on 2024-10-23
x

---

### Post by jbhardman2 on 2024-10-24
I'm beginning to believe it's something to do with Wireplumber trying to detect which sink it things would be best. When I set my wireplumber instance to debug logs, and then sleep and unsleep my laptop while tailing the log I get a ton of data but these that seam interesting:

> Oct 23 21:59:04 stanton wireplumber[2988]: T wp-event-dispatcher [event-dispatcher.c:133:wp_event_source_dispatch]: <WpEventDispatcher:0x558a046a2580> dispatching event (<0x558a04a35d30>select-target@session-item) running hook <0x558a04708470>(linking/find-default-target)

> Oct 23 21:59:04 stanton wireplumber[2988]: T wp-event-dispatcher [event-dispatcher.c:133:wp_event_source_dispatch]: <WpEventDispatcher:0x558a046a2580> dispatching event (<0x558a04a35d30>select-target@session-item) running hook <0x558a046e6a00>(linking/find-best-target)

And I wonder if "best" is overriding "default".



Am I looking in the right place? How do I get it to either not change, meaning come back on what it was last set to? Or to always choose Speaker if it has to choose something?

---

