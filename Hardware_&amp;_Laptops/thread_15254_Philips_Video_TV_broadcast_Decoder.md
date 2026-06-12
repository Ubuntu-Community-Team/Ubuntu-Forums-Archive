---
title: "Philips Video TV broadcast Decoder"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by lizardking on 2005-02-13
I have buy a  Philips Video TV broadcast Decoder in particular _SSA7130._ 
Can someone help me to install and view TV on Ubuntu?
What kind of program I should install?

thanks
 ](*,)

---

### Post by WillCooke on 2005-02-13
The driver for the saa7134 is included as part of the 2.6 kernel, so ubuntu should detect it and create a video device for it.

If you:

```
lsmod | grep tuner
``` 

You should see the module is loaded, in which case you're ready to watch TV.

Install xawtv:

```
sudo apt-get install xawtv
``` 

or use synaptic, you're choice.

Then, click Applications ->  Run Application, type in xawtv and you should be able to
see some static.  This is good.  Then you need to tune in the stations and save them.
Right click in the xawtv window and you will get a menu that will let you set your TV signal type (e.g. PAL-I for UK) and allow you to tune in.

More info here......    [http://linux.bytesex.org/xawtv/](http://linux.bytesex.org/xawtv/) 


Good luck,

Will

---

### Post by lizardking on 2005-02-14
[SIZE=3]perfect now i see TV on linux but i cannot heard any audio. I get my source input audio from tuner to microphone.So I set alsamixer to max loudenss in micorphone sectin but nothing..some help?[/SIZE]
 ](*,)

---

### Post by WillCooke on 2005-02-16
[QUOTE=lizardking][SIZE=3]perfect now i see TV on linux but i cannot heard any audio. I get my source input audio from tuner to microphone.So I set alsamixer to max loudenss in micorphone sectin but nothing..some help?[/SIZE]
 ](*,)[/QUOTE]

OK, I think this relates to a problem with the tuner chip.  

In xawtv right click in the window to get the menu up.  Where is says "Video Source" click and see if you get   a list up, if you see "for debug only" choose that.

Then, if you don't hear any audio  use the volume control applet to select line in.  That should do the job.

If your card is like mine you'll need a little cable from the line-out on the card to the line in on your sounds car.

Cheers,
Will

---

### Post by lizardking on 2005-02-22
I have a sound cable that exits from the tuner and enters in the audio board in the input of microphone.
I have already set up all the volume in the appltes. now i try the debug mode....
 

thanks you
 \\:D/

---

### Post by lizardking on 2005-02-22
[QUOTE=WillCooke]OK, I think this relates to a problem with the tuner chip.  

In xawtv right click in the window to get the menu up.  Where is says "Video Source" click and see if you get   a list up, if you see "for debug only" choose that.

Then, if you don't hear any audio  use the volume control applet to select line in.  That should do the job.

If your card is like mine you'll need a little cable from the line-out on the card to the line in on your sounds car.

Cheers,
Will[/QUOTE]
I have look i have no "for debug mode" option in video source. and i set up all volume

---

