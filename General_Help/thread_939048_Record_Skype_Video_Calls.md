---
title: "Record Skype Video Calls"
date: 2008-10-05
forum: General Help
---

### Post by bardic on 2008-10-05
Hey all,
I've been having trouble trying to find a way to record skype video convos on ubuntu. I have found it for macs and windows, so I figure there's a way but I can't find it. 

Can anyone point in the right direction, that would be great,

Thanks ^^

---

### Post by priegog on 2009-02-17
I´d also been looking for a solution to this...

---

### Post by DigitEyez on 2009-03-01
Me too.
Anyone? So far i've only been able to find programs that record the sound of a conversation.

---

### Post by Berduchwal on 2009-03-22
for recording voice in calls:
[http://atdot.ch/scr/](http://atdot.ch/scr/)

for video I do not know yet

---

### Post by sekinto on 2009-03-22
xvidcap

It is a package in the repositories and can be installed with Synaptic or apt-get.
```
sudo apt-get install xvidcap
```

---

### Post by Arisha on 2009-11-09
> **bardic said:**
> Hey all,
I've been having trouble trying to find a way to record skype video convos on ubuntu. I have found it for macs and windows, so I figure there's a way but I can't find it. 

Can anyone point in the right direction, that would be great,

Thanks ^^


As for me i use SkyCap...Because you can record the other formats..and also you can control of your records,choose level of quality .I like it's programm so much.
:lolflag:

---

### Post by Ubuntiac on 2010-01-25
So has anyone found a solution *on Linux* for this yet?

We have more open access to what happens to our data, so there's got to be a way...

---

### Post by Chronon on 2010-01-25
Maybe you could use a screencasting program like RecordMyDesktop.

---

### Post by J V on 2010-01-25
yeah recordmydesktop is great...

---

### Post by Ubuntiac on 2010-01-25
Thanks for the suggestion.

I'll give it a shot, but it seems to me that you're likely to get a fairly significant loss of quality capturing the compressed video off the screen and recompressing it again rather than using the original source. Not recompressing it would lead to much larger file sizes.

RMD and similar may be the only option though.

---

### Post by stevo1977 on 2010-02-07
Yeah, screen-capturing seems like way too many middle-men.  Does anyone know if Skycap for windows works with the Linux version of Skype?  Anyone tried Supertintin?

There is surprisingly little info about this topic on google.  I wouldn't have thought recording the webcam's stream while in a Skype call would have been that difficult.  Is it just that there's very little demand for this feature?

Thanks.

Cheers,
stevo

---

### Post by stevo1977 on 2010-02-10
Not to spam this thread, but I had hoped to do a presentation this weekend on skype AND to record it for instructional purposes later.  The window of my own webcam on skype is way too small for a screencap to do the job.

No one has found any solutions natively in Linux for recording the webcam stream while running skype?  I thought about running SkypeCap or Vodburner along with skype under Wine, but skype wouldn't install under Wine.

Cheers,
stevo

---

### Post by Ubuntiac on 2010-02-11
VLC -> File -> Convert / Save -> Capture device

It just won't capture the other parties video in a Skype call. Works fine for just capturing *your* webcam though.

---

### Post by stevo1977 on 2010-02-11
Thanks, ubuntiac.  I went through VLC's capture dialog and when I clicked 'Save' nothing happened.  I made sure it was capturing the same cam as skype (/dev/video0) and told it where to save the files and everything.  When I tried to Media>Open Capture Device, it said it couldn't access the vl42 driver (or whatever its name is), I imagine b/c skype was using it.  Are you sure they can work at the same time?  Maybe I just need to read more of the help files on VLC.

Thanks for the suggestion.  Any more help you could give would be much appreciated.

Cheers,
stevo

---

### Post by Ubuntiac on 2010-02-11
To tell the truth, I'd used VLC without Skype and assumed it would still work the same with it running :(

D'oh!

---

### Post by stevo1977 on 2010-02-11
Ah, well, good idea anyway.  Thanks for sharing.  Maybe if I could tell VLC to use a different driver, they could both access the same hardware?  That doesn't sound very likely.

Man, I didn't think this would be that difficult when I first considered it.

Cheers,
stevo

---

### Post by glavkos on 2010-09-02
> **Ubuntiac said:**
> VLC -> File -> Convert / Save -> Capture device

It just won't capture the other parties video in a Skype call. Works fine for just capturing *your* webcam though.


Do one has to fix the settings ..name of video device or anything else?):P

---

### Post by Ubuntiac on 2010-09-03
> **glavkos said:**
> Do one has to fix the settings ..name of video device or anything else?):P

Sorry. We realised further up in this thread, that recording video this way only works... when Skype isn't running! *sigh* I'm still looking for a way to do this... :(

---

### Post by sohlinux on 2010-10-27
has anyone successfully recorded skype audio and video with ubuntu yet?

---

### Post by herovern on 2010-11-15
I'm ok to use any skype alternative to be able to record video call.
Is there such possibilities for another video conferencing software?

---

### Post by niceguy123 on 2011-01-13
hello everyone,

Any developments of capturing Skype on Ubuntu? I would like to be able to record myself while on the skype conference. 

I am trying with a couple of applications but so for haven't gotten far. 

I just installed Webcamstudio but haven't figured out how to record webcam in it.

Xvidcap - I have recorded video, but don't see an option for it to record audio. Can it do that?

VLC - (regardless to Skype), I have succeeded in recording video but not audio, how do I tweek VLC to record audio too?

Thanks

---

### Post by coldraven on 2011-01-13
How about Kazam?   [http://www.omgubuntu.co.uk/2010/12/record-screen-linux/](http://www.omgubuntu.co.uk/2010/12/record-screen-linux/)

It worked well for me but I did not have Skype running.
Then I squeezed it through Handbrake and got a good quality m4v

---

### Post by niceguy123 on 2011-01-13
> **coldraven said:**
> How about Kazam?   [http://www.omgubuntu.co.uk/2010/12/record-screen-linux/](http://www.omgubuntu.co.uk/2010/12/record-screen-linux/)

It worked well for me but I did not have Skype running.
Then I squeezed it through Handbrake and got a good quality m4v

Yes, Kazam is neat. Thanks for bringing that to my attention. It would be great if it could film via the webcam too.

---

### Post by feelmjawlk on 2011-08-03
This is also a problem for me.
I have telepresence conferences over skype and I'd like to record the meetings for future reference.


Is there any video-conference (2 part is ok for me at the moment but 2+ would be even better) software that supports saving the video-conversation out of the box?
Cross-platform is a plus of course since the other party usually is on a Windows machine.

---

