---
title: "One-touch-keys (multimedia keys) on HP 6710b"
date: 2008-05-16
forum: Hardware
---

### Post by Visitor.Q on 2008-05-16
Hi,

I installed Ubuntu Hardy two days ago on my HP 6710b laptop and everything worked fine out-of-the-box. However, I installed some stuff and other things happened, and then suddenly the touch-keys (or multimedia keys, if you like) above my keyboard would not work anymore. (Keys are for 'help', 'wlan on/off', 'presentation', 'mute' and 'dec/inc volume'). So, I have searched through bug reports and programs like keytouch, but it didnt work out. 
Is the driver for this something that has to be found in xorg.conf? Because it worked the first time, I know Ubuntu can do it (although pressing the mute key would not work perfectly; the sound is turned on a few moment later).
I tried 
```
sudo tail -f /var/log/acpid

```
while pressing the buttons, got no signals. Setting the keys in system>preferences>keyboard shortcuts didnt work, the application didnt notice that I pressed any of these buttons. Where can I start to find what the problem is? Thanks!

Oh, the led lights in the button do light up when I touch them.

---

### Post by Visitor.Q on 2008-05-16
It seems that the keys don't work under the factory installed Vista as well...

---

