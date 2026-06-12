---
title: "Pulseaudio update"
date: 2018-03-08
forum: Hardware
---

### Post by angel mike on 2018-03-08
When I update pulseaudio using the terminal I get version 8 but I notice there is a version 11.1 that has been issued.

---

### Post by gordintoronto on 2018-03-08
There are often occasions when the Ubuntu team has not confirmed that a new version of an application is secure and works.

---

### Post by angel mike on 2018-03-09
Thanks gordintoronto for response - just surprised there is so much difference between the versions. There appears to have been some improvements in the Bluetooth application - which is what I am trying to improve.
Mike

---

### Post by mc4man on 2018-03-09
pulseaudio 11 will only be available in 18.04, 16.04 has 8 though it's received numerous updates since 16.04's release, many concerning bluetooth.
Don't see that much difference here in *my bluetooth use case*, in 16.04 auto-connect hasn't been enabled but that easily done user side.

In regards to auto-connect (a speaker here) both 18.04 & 16.04 modified used to work perfectly, now for both only if speaker is turned on after login.
somehow the discover > auto-connect has broken down when speaker is on during boot (- that's easily solved via a startup script

---

### Post by angel mike on 2018-03-10
Thanks mc4man - I get the picture. Can you elaborate a bit more on the speaker control?
 I have lost sound on my dell laptop in trying to get bluetooth to connect to my powerbeats ear plugs.

---

### Post by angel mike on 2018-03-10
I have used the Alsa Info site which has given the following output 
Can someone manage to have a look at it to see if ALSA is loaded correctlty ?

[http://www.alsa-project.org/db/?f=120e1677c09a82b848f75319cf5652d383e5f000](http://www.alsa-project.org/db/?f=120e1677c09a82b848f75319cf5652d383e5f000)

I did originally purge/reinstall Alsa and Pulseaudio. Perhaps not the wisest of things to do.

---

### Post by angel mike on 2018-03-10
It seems my problem with pulseaudio might be down to permissions since running pavucontrol gives

  	 	 	 	   [A popup box appears with]
Establishing connection to PulseAudio. Please wait.  

[https://unix.stackexchange.com/questions/265043/problems-with-pulseaudio-pavucontrol-and-pacmd-not-connecting-to-pulseaudio](https://unix.stackexchange.com/questions/265043/problems-with-pulseaudio-pavucontrol-and-pacmd-not-connecting-to-pulseaudio)

---

