---
title: "Toshiba Ali winmodem fails handshake."
date: 2008-07-25
forum: Hardware
---

### Post by Perkins on 2008-07-25
I installed sl-modem-daemon, and I managed to get it to find my modem, but then things got weird.  If I open up a terminal emulator and issue an ATDT command, it takes the phone off-hook, hears the dialtone, and dials the number I give it.  When the other end answers, it plays the handshake tones, but instead of playing them quickly, each part of the sequence lasts about two seconds...  Needless to say, the handshake fails.  

slmodemd seems to only use a tiny portion of the AT command set, so lots of the settings I would normally try adjusting are not available, and the information commands do not return anything useful.

Has anybody else had this problem?  I'm using a Toshiba Portege with an Ali soundcard/modem combination thing.

---

### Post by phidia on 2008-07-25
Since you know your way around AT&T commands you can install minicom (it's in the repos) and play with that. If you're using a gui then you probably want to install gnome-ppp too. Have you went over the docs [here]("https://help.ubuntu.com/community/DialupModemHowto") to see if you can get the modem working correctly?

---

### Post by ModelM on 2008-07-25
The only thing I can think of is make sure the proper country is set. I think there are commands in the daemon to read & set the country code.

---

### Post by Perkins on 2008-07-26
I'm using cutecom, but to each his own I guess.  :P  I'm pretty sure I have the country set properly.  At least, I put in USA as the parameter when I start the daemon and it doesn't return an error message.  I've never heard a modem handshake from a different country, so I'm not able to tell if it matches anywhere else.  Some of the older modems I've seen have to be set for client or server, but those commands don't seem to work with the program.

---

