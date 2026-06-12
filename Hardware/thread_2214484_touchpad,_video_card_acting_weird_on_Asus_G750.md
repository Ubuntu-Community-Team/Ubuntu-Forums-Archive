---
title: "touchpad, video card acting weird on Asus G750"
date: 2014-04-01
forum: Hardware
---

### Post by gatesdrovme2it on 2014-04-01
I am running Ubuntu  12.04 LTS and I have had a lot of issues with the touchpad. This helped  to fix my inability to right-click with the right button of the  touchpad:

  [http://superuser.com/questions/61958...rking-in-linux](http://superuser.com/questions/61958...rking-in-linux)

  Now my biggest problem is that I have to really bang on the touchpad  to make it click. I don't mean the buttons but the touchpad area itself  is not sensitive AT ALL in spite of having the sensitivity cranked up in  the system tools/mouse and touchpad.
  Also sometimes even when I bang on it hard, it is only the second or  third click that is recognized, not the first. This makes the click  feature of the touchpad almost worthless.


  I have the speed and acceleration turned all the way up but I would  like the cursor to move faster, accelerate faster, and move more with  each swipe on the touchpad since I have a big screen to cover (17inch).
  Any ideas? Also the touchpad does not completely turn off while  typing. Or it doesn't turn off long enough. The cursor wobbles all over  as I type.


  So, yeah, this touchpad is a nightmare with the G750 in Ubuntu.


  Another thing is the video card. When I scroll, I see a wonky line in  the middle of the screen, going horizontally. I tried using the  built-in method to update the video driver, but it didn't help even  though it installed the driver.
  I should mention too that using the touchpad I can't select multiple  files in a series using either shift-click or ctrl-click. This is really  frustrating! 
  Any help for these problems would be much, much appreciated.

---

### Post by varunendra on 2014-04-05
The link you provided is broken, please correct it.

As an alternative to "Disable Touchpad while typing", you may try making Palm detection more sensitive as suggested in this thread (posts #2 and #4) : [http://ubuntuforums.org/showthread.php?t=2212010](http://ubuntuforums.org/showthread.php?t=2212010)

It may also help if you post the outputs of -
```
xinput
synclient
```

Please use 'Code' tags while posting the outputs (follow the "Use Code Tags" link in my signature if needed).

---

