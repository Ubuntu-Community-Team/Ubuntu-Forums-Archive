---
title: "not a 7 inch but a 37inch sharp?"
date: 2014-09-23
forum: Hardware
---

### Post by joe136 on 2014-09-23
I have had this early 37" sharp hdtv as my monitor with ubuntu for years and have always had it show up as a 7" sharp..this was no problem for some time but now every one thinks I'm on a phone. ( I have poor vision and must blow up everything)
any ideas on how to tell ubuntu  that this is a 37" sharp hdtv not a 7"  sharp?
thanks joe

---

### Post by grahammechanical on 2014-09-23
I have the same on my recently purchased Sharp 24" digital TV. Digital TVs and monitors have something in their electronics called Extended Display Identification Data (EDID). This EDID is read at the start of the OS loading and Linux gets the optimum settings for the monitor from it. It also gets the make and model from the EDID.

It is my guess that the code in the Sharp EDID is faulty in some way.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

Regards.

---

### Post by joe136 on 2014-09-23
By the way also have dell monitor hooked up/ dual display on a
8 core amd  / gigabyte ga 880  /  16 gig ram

---

### Post by joe136 on 2014-09-24
granted ed id is faulty...now how to fix edit this data and tell it I am not n a phone with a 7' screen?

---

### Post by joe136 on 2014-09-25
anyone know how to edit the Extended Display Identification Data?
I found this page [http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor) 
then I installed   /read-edid_3.0.1-2_amd64.deb
ran prog and got:

sudo get-edid
[sudo] password for joe: 
This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0xc01c8 "ATI ATOMBIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;    x
&#58467;TL&#65533;&PTrQ&#65533; n(U&#65533;Z&#65533;
&#1034; &#65533;->&#65533;(&#65533;SHARP HDMI
  &#65533;8=.
EDID claims 1 more blocks left


*********** Something special has happened!
This happens a lot with TV's, and other devices
with extension blocks. If you have a TV, don't bother.
Otherwise, please contact the author, Matthew Kern
E-mail: [EMAIL="pyrophobicman@gmail.com"]pyrophobicman@gmail.com[/EMAIL]
Please include full output from this program (especially that to stderr)



Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

      j&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;    x
&#58467;TL&#65533;&PTrQ&#65533; n(U&#65533;Z&#65533;
&#1034; &#65533;->&#65533;(&#65533;SHARP HDMI
  &#65533;8=.
EDID claims 1 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
      jLooks like VBE was successful. Have a good day.
joe@xxxxx:~$ 



what's next? what about  parse-edid         a little help..
does anyone know beans about this? I use to have a few more beans..
tnx



ok.    let me add this... two days latter
after :researching edid problem some more I found this page 
[http://ubuntuforums.org/showthread.php?t=1779988](http://ubuntuforums.org/showthread.php?t=1779988) where
he wrote this :

ay! I've Solved it! Yesss! Just like every other Linux user knows how it  feels to fix an annoying issue, I can finally say the same.

Just for reference, I'll explain my steps.

Requirements: The use of wine for Phoenix Designer and Moninfo. And the know-how of editing xorg.conf

I had to extract a valid EDID using Phoenix Designer. Saved as .raw  file. Used MonInfo to open edid.raw. Found monitor's modelines in  moninfo. Copied modelines into xorg.conf under the monitor section.  Rebooted. Viola! 

Trust me, it wasn't that easy to do before I knew how. I just can't  believe there hasn't been a clear cut precise way to fix this issue yet.  Not saying my instructions are as such, it's just that I had to bounce  from forum to forum, thread to thread, just to get bits and pieces of  "fixes" to actually get a solution. But, finally, as a great man once  said, it is finished.


before I try to jump through these hoops...
any thoughts ......any easier way ?

---

