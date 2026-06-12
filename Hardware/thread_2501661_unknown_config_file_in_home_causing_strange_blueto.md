---
title: "unknown config file in home causing strange bluetooth behavior"
date: 2024-10-16
forum: Hardware
---

### Post by outofcheese on 2024-10-16
--removed--
irrelevant after logging in as a dummy user

The gist is: a BT amp doesn't connect properly in my main user account but does so when I log in as a dummy user.
The device is a Fosi Audio BT20A and it is the only device I can't properly connect to (from ym main account that is).

---

### Post by outofcheese on 2024-10-16
I'll add the output of journalctl --user -u wireplumber

```
16 17:43:37 gamera wireplumber[3430]: Failed to release transport /org/bluez/hci0/dev_F4_4E_FD_8E_6A_07/sep2/fd1: Method "Release" with signature "" on interface "org.bluez.MediaTransport1" doesn't exist
Okt 16 17:44:03 gamera wireplumber[3430]: 0x603f5ccac4a8: error 24
Okt 16 17:44:03 gamera wireplumber[3430]: Failed to release transport /org/bluez/hci0/dev_F4_4E_FD_8E_6A_07/sep2/fd2: Method "Release" with signature "" on interface "org.bluez.MediaTransport1" doesn't exist
Okt 16 17:44:30 gamera wireplumber[3430]: 0x603f5ccac4a8: error 24
Okt 16 17:44:30 gamera wireplumber[3430]: (bluez_output.F4_4E_FD_8E_6A_07.1-67) running -> error (Received error event)
Okt 16 17:44:30 gamera wireplumber[3430]: Failure in Bluetooth audio transport /org/bluez/hci0/dev_F4_4E_FD_8E_6A_07/sep2/fd3
```

---

### Post by outofcheese on 2024-10-20
One step forwards, two steps back: I logged into a dummy user account and the Fosi Audio device behaves normally (registers as audio, audio transport is enabled, sound is playing, no disconnects). This made me delete all "pulse" remnants in my main accounts config files in the home directory, since the system is clearly working and the problem can only be something located in my home. So   .pulse/* .config/pulse/* .pulse-cookie .config/jack/*  are gone now. Still the Fosi Audio shows the same behavior. Does anybody have an idea what (old) configuration in my home could cause this/I should get rid of? My /home is always on a separate partition and has seen many Ubuntu releases so there could be useless/harmful configs left.

---

### Post by outofcheese on 2024-11-17
Finally, I found it!
I purged the device MAC from ~/.local/state/wireplumber/default-nodes and ~/.local/state/wireplumber/default-profile , now it connects flawlessly again. Since I did both back to back without checking inbetween I can't say which of the two was the culprit but something wrong got saved in one or both of those files and prevented the bluetooth amp from connecting properly only with that user logged in.
I hope this information can help somebody who got into the same pickle.
Cheers!

---

