---
title: "Cannot achieve HDMI screensharing with Lubuntu 22.04 LTS"
date: 2023-06-26
forum: Hardware
---

### Post by AbleTassie on 2023-06-26
I installed Lubuntu 22.04 LTS several days ago. I would like to share my PC screen now via an HDMI cable to my TV. When booting up with the HDMI cable plugged in, the TV does show some of the screens on the PC when booting up and the TV also shows the Sign In Screen that has the Lubuntu Insignia with the slot for the password for the sole user (me). But as soon as I sign in the screen sharing effectively stops: I get a blue screen with some clouds, but no desktop icons or touchpad cursor. 

When I unplug the HDMI cable, I the TV screen goes blank and says "no signal" and the taskbar appears at the bottom of the PC screen and the PC desktop icons rearrange too. Plugging the HDMI cable back in reverses the effects: blue sky screen with clouds on the TV, but no real screen sharing to the TV and loss of taskbar and rearrangement of icons on the PC screen.
 
I figure the solution to the problem must have something to do with the Lubuntu PC Monitor Settings. So I have tried to change the monitor settings with the HDMI cable plugged in. When I do this, the PC is sensing the TV, because it is giving me the TV Make and Model and the correct HDMI port on the TV. But I have been unable to really get screen sharing by fiddling with the Monitor settings/preferences. 

I am thinking that the blue sky with clouds I am getting on the TV is some kind of generic screen. Because even though the blue sky with some clouds is similar to the Lubuntu screen, I don't think I am getting screen sharing for just part of my PC screen, because when the PC screen is "full" of another screen there is no change to the TV screen. And there is no audio coming through the TV when there is audio on PC via youtube.

Does anybody have any idea what is wrong or what I should do?

Thanks,

A.

---

### Post by AbleTassie on 2023-06-26
I have continued to work on this problem and changed the background screen on the PC and now that new background screen is coming through on the TV but it appears to be out of focus and only part of the PC screen appears to showing on the TV.  Also now there is a movement of the mouse pointer on the TV screen. But I have no mouse pointer in this PC screen that I am writing this reply on. I am thinking that perhaps there are two problems: 1) there are 4 different desktops in Lubuntu and the TV is only picking up one of them, even though I am looking at another one of the 4 desktops on the PC (I am not sure which desktop I am on -- I would actually like to eliminate all the desktops, I find them annoying) and 2) the PC monitor settings are such that only a part of PC screen (which is also out of focus) is showing up on the TV screen.

Update: Suddenly I have the mouse pointer back on the PC screen, but it is now gone from the TV. I wonder why.

Again, if anybody has any insight into the problem I would appreciate advice. 

A.

---

### Post by AbleTassie on 2023-06-26
OK, I improved the situation immensely by putting "monitor settings" in the search box (in the lower left hand corner, you can also hit the "Windows Key" and the slot to enter the words "monitor settings" comes up). Then I had to adjust the "x" and "y" settings and the "Apply" and "Save" buttons made a lot more sense. You are given about 10 seconds to accept (apply or save) the settings while looking at the monitor to see if the settings are good. In the end I set both "x" and "y" to 0 and I set the resolution of the TV screen to be the same resolution as the PC screen and now I appear to have good screen sharing including with the mouse pointer on both the PC and TV screens. 

And the screen I am working on now to write this post is also showing up on the TV. If I can assure that I am getting sound, then hopefully I can mark the thread as SOLVED.

A.

---

### Post by AbleTassie on 2023-06-26
I have now managed to get the audio sharing through the HDMI working with Lubuntu 22.04 LTS using the following method: hit the Windows button or click on the Lubuntu insignia/icon at the bottom left corner of the screen > Sound & Video > PulseAudio Volume Control >Configuration tab > Profile (checked)  using the drop down menu select "Digital Stereo (HDMI 2) Output + Analog Stereo Input." If you then go to the Output Devices Port shows: HDMI/DisplayPort 2 (plugged in) and you can see the volume signal on a visual meter. 

So at this point, I have managed to get the HDMI screen sharing and audio sharing working on one of my TVs. I hope to get this same screen and audio sharing working on another TV  that I have. It may be that I will need to use much the same methods for the other TV.

[I]Edit several minutes later: I got the screen sharing going with the other TV using the same method described above. The audio worked on the other TV without me doing anything.

Edit 1 day later: I had to go back into the settings to get the audio to work with the laptop's own speaker when watching a youtube video. Specifically live ("Windows") key > Sound &Video> PulseAudio Volume Control > Configuration tab>Analog Stereo Duplex (on the drop down menu with Profile checked) > Output Device tab Port Speakers.
[/I]
Thanks,

A.

---

### Post by AbleTassie on 2023-09-26
I had to monkey around with the monitor settings again, because somehow something happened. And I was able to get the large screen TV that is hooked up via an HDMI cable to my laptop and the laptop monitor settings in a good place by going to "Monitor Settings" (hit the "Windows" key and search "Monitor Settings") > Fast Menu > Fast Options > 1 1 Unified View. See attached screenshot below.

Able


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292796&stc=1[/IMG]

---

