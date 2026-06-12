---
title: "Hotkeys are sent to acpid log"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by AndersRiggelsen on 2007-05-16
Hi there.

On my laptop (running vanilla Ubuntu 7.04) some of my hotkeys are working fine, but most doesn't. I noticed that they are dumped into the acpid log when I press them.

I get these kinds of messages:

[Wed May 16 15:46:47 2007] received event "hotkey HOTK 0000005c 00000005"
[Wed May 16 15:46:47 2007] notifying client 4750[0:0]
[Wed May 16 15:46:47 2007] completed event "hotkey HOTK 0000005c 00000005"

When running a 'ps' to find out who 4750 is, I get this:
 4750 tty7     00:01:32 Xorg

So why can't "Keyboard Shortcuts" detect the buttons at all?
I tried running 'xev' to test raw input and it doesn't detect the presses either.
How can I make Ubuntu recognize those key presses?

Thanks

---

### Post by AndersRiggelsen on 2007-05-24
Doesn't anyone have an idea how to redirect the event to some app that can understand it?
(sorry for bumping, but it can be quite frustrating) :(

---

