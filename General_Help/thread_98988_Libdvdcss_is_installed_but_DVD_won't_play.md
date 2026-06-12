---
title: "Libdvdcss is installed but DVD won't play"
date: 2005-12-04
forum: General Help
---

### Post by randcoop on 2005-12-04
DVD's aren't playing.  I've tried Kaffeine, Mplayer, Totem, and VLC.  I've installed libdvdcss2 and 3.  The error message is nearly the same for all players: can't read/maybe don't have permissions/file encrypted.

DVD is /dev/hdc.  Can be mounted on /media/cdrom0.  Or not.  Tried running the players and then loading the DVD and also tried from command line ([program name] dvd://dev/hdc

Nothing works.

Any suggestions would be much appreciated.

---

### Post by teaker1s on 2005-12-04
look [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29") 

could be ccs which above link deals with
you could search automatrix which is on forums to install dvd playback etc

you will also need dma enabled

---

### Post by doitashimashite on 2005-12-04
What does

ls -l /dev/dvd

show you? Should be something like:

lrwxrwxrwx  1 root root 3 2005-12-04 22:31 /dev/dvd -> hdc

If it says this instead:

ls: /dev/dvd: No such file or directory

then type

sudo ln -s /dev/hdc /dev/dvd

Finally, to enable dma on this drive:

sudo gedit /etc/hdparm.conf

add the following:

/dev/hdc {
dma = on
}

---

### Post by randcoop on 2005-12-05
/dev/dvd points correctly to hdc.  DMA is on.

Still getting the same response: can't read encrypted DVD.

Is it possible that the libdvdcss files didn't install properly (usd libdvdread3 to install them)?  Should I remove them and then re-install them using apt-get only?

Is there anything else anyone can think of?

---

