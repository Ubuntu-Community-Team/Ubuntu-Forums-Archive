---
title: "looking for Realtek audio HD codec for linux core up to 4.x"
date: 2017-11-10
forum: Hardware
---

### Post by calibal on 2017-11-10
Hello :)

Is someone have the realtek audio HD codec witch can work on linux core up to 4.x (4.16 to be exact)

the one on the realtek website are for core 2.x and 3.x.

the codec are here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

i've tried to compile the  "Linux driver (3.0) v. 5.18rc8" on ubuntu 17.10. the comand

```
./compile with-card=hda-intel 
```
seem to be ok.
but the
```
make
```
is outputting error code 2. i think it's mainly because it's not for this core version.

it's for the asus mini transformer T102HA.

All other things seem to work correctly, except the sound.

thanks by advance for your help.

---

