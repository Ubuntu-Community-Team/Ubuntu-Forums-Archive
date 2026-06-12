---
title: "LIRC config totem - Zoom i video"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by jayleesan on 2009-08-23
Hi All,

I managed to set up LIRC on Totem using the Mythbuntu package for it but found there's little options for controling Totem. Just the basic commands.

I managed tot edit ~/.lirc/totem and add controls for fullscreen, previous and next by adding these lines:```

begin
    remote = mceusb
    prog = totem
    button = Home
    config = fullscreen
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = totem
    button = Replay
    config = previous
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = totem
    button = Skip
    config = next
    repeat = 0
    delay = 0
end
```
... which is great!

:confused: Now the thing I'm missing is the abbility to control zooming in and out of the video, which is possible by pressing R and T on the keyboard.

Can anyone share the configuration to make my remote zoom vid's in Totem?

---

### Post by jayleesan on 2009-08-25
Anybody?

---

### Post by jis on 2011-06-23
One option is to install lirc-x and configure buttons to simulate keypresses. Config entries could be something like this:
```

begin
       prog = irxevent
       button = DVD_Zoom
       config = Key R CurrentWindow
end

```
irxevent should be running for this to work.

However, it would be better, if we could find totem specifig config commands. Can anyone find a list of commands for totem?

---

