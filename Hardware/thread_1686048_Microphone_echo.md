---
title: "Microphone echo"
date: 2011-02-11
forum: Hardware
---

### Post by bobblues on 2011-02-11
Ubuntu 10.10 When using an external microphone sound recording echo's. If I record 1234 when play back I get 1-1 2-2 3-3 4-4. Each sound is replicated two to three times. I have been through all my settings in in sound preferences to no avail. I installed alsa mixer. that did not help or change the concern. No idea where to go from here. Are there any ideas out there?:(

---

### Post by lunalobo on 2011-04-06
I have the same problem. 
I have 11.04 and I get the same symptom with Sound Recorder.
I say one, two, three, and it comes back one - one, two - two ,three - three. 
Tried various combinations in the Sound preferences app. to no avail.
I need to get this right so that I can get Skype working.

---

### Post by lidex on 2011-04-06
> Sound can be heard but with an echo
    This happens particularly with applications where there is both input ad output, for example voice chat or voice IP ones, and you are using some chipset like the Intel ICH ones.
    If this happens it probably happens only with a few chipsets: the cause is that those chipsets allow more than one capture source channel to be specified, usually two, and the two are different.
    This can only be checked looking at non simplified controls with amixer, for example with:

    amixer cget name='Capture Source'

    which might return:

      ; type=ENUMERATED,access=rw---,values=2,items=8
      ; Item #0 'Mic'
      ; Item #1 'CD'
      ; Item #2 'Video'
      ; Item #3 'Aux'
      ; Item #4 'Line'
      ; Item #5 'Mix'
      ; Item #6 'Mix Mono'
      ; Item #7 'Phone'
      : values=0,5

    This indicates that there are 8 possible capture channels, and values=0,5 indicates that both Mic and Mix are enabled at the same time. This often is the result of a bug in alsamixer.
    If this is not intentional, it is possible to ensure only one channel is enabled for capture by setting both values to the same number, for example for Mic in this case with:

    amixer cset name='Capture Source' 0,0



Reference:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#trouble](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#trouble)

---

### Post by lunalobo on 2011-04-06
LIDEX,

I dont actually understand all that you say but I did run your query string in a terminal I got several items: mic, cd, video, aux, line, mix, Mic Mono, phone but also got values=0,0.

So I supose this is still happening with these settings.
I will look at the suggested http link but I can see there is a lot to learn.
Is there anything else I could try?
My hardware is a HP Presario 2565EA

---

### Post by smithark on 2011-04-07
> Sound can be heard but with an echo
This happens particularly with applications where there is both input ad output, for example voice chat or voice IP ones, and you are using some chipset like the Intel ICH ones.
If this happens it probably happens only with a few chipsets: the cause is that those chipsets allow more than one capture source channel to be specified, usually two, and the two are different.
This can only be checked looking at non simplified controls with amixer, for example with:

amixer cget name='Capture Source'

which might return:

; type=ENUMERATED,access=rw---,values=2,items=8
; Item #0 'Mic'
; Item #1 'CD'
; Item #2 'Video'
; Item #3 'Aux'
; Item #4 'Line'
; Item #5 'Mix'
; Item #6 'Mix Mono'
; Item #7 'Phone'
: values=0,5

This indicates that there are 8 possible capture channels, and values=0,5 indicates that both Mic and Mix are enabled at the same time. This often is the result of a bug in alsamixer.
If this is not intentional, it is possible to ensure only one channel is enabled for capture by setting both values to the same number, for example for Mic in this case with:

amixer cset name='Capture Source' 0,0

what he is trying to explain is that in the list below, see the last line (coloured red):
; type=ENUMERATED,access=rw---,values=2,items=8
; Item #0 'Mic'
; Item #1 'CD'
; Item #2 'Video'
; Item #3 'Aux'
; Item #4 'Line'
; Item #5 'Mix'
; Item #6 'Mix Mono'
; Item #7 'Phone'
: [COLOR="Red"]values=0,5[/COLOR]

it means both '0' (Mic) and '5' (Mix) are enabled as sound capture devices. to disable the echo, you have to remove one of the above.
in order to set 'Mic' as your sound capture device, run: "amixer cset name='Capture Source' 0,0".

i hope now its clear. correct me if i am wrong.

---

### Post by lunalobo on 2011-04-07
Smitharc

Thanks, 

but I do understand that, and I am understanding more as I play, but I said that my value is 0,0 so it looks like the mic is only selected and I am still having the echo.
But I don't know what to do now. Is there some other setting I can look at?
I can see the mixer is a conexant cx20468.

---

### Post by lidex on 2011-04-08
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by lunalobo on 2011-04-10
Lidex,

I have done as you suggested and I have got this url and this info.
alsa.txt that I hope I have managed to upload it.

or 

this is the url given to me running that script.

[http://www.alsa-project.org/db/?f=fee8ba6407dc2dbbe0e6cb2875e6b30131d2405f](http://www.alsa-project.org/db/?f=fee8ba6407dc2dbbe0e6cb2875e6b30131d2405f)

At the moment doesn't mean much to me. Not sure what I am looking for.

---

### Post by lidex on 2011-04-13
> **lunalobo said:**
> Lidex,

I have done as you suggested and I have got this url and this info.
alsa.txt that I hope I have managed to upload it.

or 

this is the url given to me running that script.

[http://www.alsa-project.org/db/?f=fee8ba6407dc2dbbe0e6cb2875e6b30131d2405f](http://www.alsa-project.org/db/?f=fee8ba6407dc2dbbe0e6cb2875e6b30131d2405f)

At the moment doesn't mean much to me. Not sure what I am looking for.

How old is this thing? You ever update the bios? Does it work in an official release? You know this is beta right, and when running the development version you are only supposed to post problems to the development forum?

---

### Post by lunalobo on 2011-04-18
Hi,

Hey, I am older than this. Gulp! I was born when there were crystal sets and steam trains for real.

It was bought in 2004. Nots so long ago.  I want to use this as an internet radio and telephone (skype). I want to freely move my old laptop about the house. That is why I am interested in removing the echo when I use the mike. I actually did have 10.10 but I thought 11.04 was more stable on the Wireless. But it isn't I have gone back to 10.10.
 
Later I 'll run your script on 10.10.

Results at [COLOR="Red"]http://www.alsa-project.org/db/?f=caa62ed8b1b5359ef4fd186e9b7724569854999b[/COLOR]

---

