---
title: "multimedia/special buttons stopped working"
date: 2009-06-29
forum: Hardware
---

### Post by sdlynx on 2009-06-29
Hello everyone,

When I first installed ubuntu 9.04 the media keys I had worked perfectly.. now for some reason none of the buttons work (I have an HP dv5-1251nr with quickplay, mute, volume up/down, back, play/pause, forward, stop, and wireless buttons).  The only two buttons that seem to register at all are the volume up and down buttons and even then they act strange (I'll push volume down and the volume will go down but when I let go of the button it goes back up, same for volume up). Each of the buttons used to work fine.  I used 'xev' to see if the buttons were working and only volume up/down registered also.  I dpkg-reconfigured evdev to see if that was the problem but the problem persists. I know I have seen many forums showing solutions but none of them worked and I'd rather not use keytouch as it seems to mess up other keys on my computer.

EDIT: Sorry for making this useless thread I fixed it by going into System > Preferences > Keyboard and the layout wasn't set to USA so I did that and changed the model to mine.  At least this may help some other people if they need help...

---

