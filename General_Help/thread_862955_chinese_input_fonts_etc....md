---
title: "chinese input fonts etc..."
date: 2008-07-18
forum: General Help
---

### Post by benner on 2008-07-18
i jut installed hardy for a taiwanese friend and installed chinese suport and east asian characters input.  she has tried most of the keyboard input options and most of them aren't working.  the phonetic bits come up (pinyin or bo po mo fo) but when i select the one i want, it omes up blank on the openoffice document.  she has been doing this for a long time on windows and trying all the tricks she knows are not working here.  i assume there are missing fonts or something but there is a lot to choose from in the repositories.  has anyone written a good script to get everything set up nicely?  or does anyone have a suggestion?  thanks in advance...

---

### Post by Viper666 on 2008-07-18
did u also install...
[B]scim 
scim-gtk2-immodule ?[/B]

u may also need
[B]scim-hangul
scim-pinyin
scim-chewing
scim-tables-zh[/B]

---

### Post by benner on 2008-07-18
yes, scim is all set up.  when i use it the chinese characters don't appear on the page.  the input part seems to be there.  the output isn't, i guess.

---

### Post by Viper666 on 2008-07-18
try some other fonts maybe?

these look the best in my opinion (for Chinese input)
ttf-arphic-bsmi00lp
ttf-arphic-gbsn00lp
ttf-arphic-ukai
ttf-arphic-uming

---

### Post by benner on 2008-07-18
the simplified works (at least erbi and wubi) but everything for simplified characters is not working.  the options come up fine but when you select the one you want, it appears blank on the page.  she is taiwanese and will use the traditional characters with bo po mo fo input methods such as ZhuYin.  i can't get them to work.  thanks  so far for your help.

---

### Post by benner on 2008-07-18
chinese input continues to suck in ubuntu. i have installed every chinese package and metapackage there is and i am still getting squares and squiggles where there should be characters.  with a billion people, a rapidly growing market and massive pressure from the US to stop pirating software, it is ridiculous that chinese doesn't work out of the box. 

as an outspoken advocate, it is frustrating when you are on the verge of converting someone and then something simple and stupid gets in the way, whether it is wireless, a touchpad or in this case the most widely spoken language on earth. 

now that i have had my rant, can someone help me get these fonts to appear?

---

### Post by Viper666 on 2008-07-18
maybe something suites your problem...

[http://ubuntuforums.org/showthread.php?t=582424]("http://ubuntuforums.org/showthread.php?t=582424")
[http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/")

---

### Post by benner on 2008-07-30
a lot of satisfied customers in that thread (up to gutsy) but the post at the end of the thread says it doesn't work in hardy. i'm still getting some characters coming up with little boxes with numbers in them where there should be characters.

still workin' on it. but thanks folks.

---

### Post by seshomaru samma on 2008-08-13
what i would do is use the hong kong repos and download any possible font
```
sudo apt-cache search chinese
```
maybe reinstall scim as well
if this doesnt work then post on the scim forum
i'm using hardy (on an english session) and didnt encounter these problems

---

### Post by lanruisen on 2009-01-20
[http://www.debian.org.tw/index.php/scim](http://www.debian.org.tw/index.php/scim)

[http://ubuntuforums.org/showthread.php?t=528382](http://ubuntuforums.org/showthread.php?t=528382)

These two threads got my Chinese working very well

---

