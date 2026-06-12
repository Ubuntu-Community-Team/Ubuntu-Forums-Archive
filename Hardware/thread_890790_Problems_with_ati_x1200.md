---
title: "Problems with ati x1200"
date: 2008-08-15
forum: Hardware
---

### Post by rogorido on 2008-08-15
hi!

I have the following question for the forum. Maybe there is anyone who can help me.

I have the following system:

* gutsy (problem also with hardy) with kernel 2.6.22-14
* ATI Technologies Inc Radeon X1200 Series
* driver: compiled from the last ati driver released by ati.com

The situation: compiz (or KDE 4.1 effects) DOES WORK.

BUT: I have a problem which is not easy to explain (even not in Spanish, my mother language). The problem is that I have a kind of flickering which consists on a line (but not a visible one!) which goes diagonally from the top of the screen to the bottom.

I know: it is very strange. But I think it has to do with some configuration in the xorg.conf (there are LOTS of options!). It also has to do with the following message in xorg.0.log:

(WW) AIGLX: 3D driver claims to not support visual 0x23
[repetead many times with differents numbers]


The options I set in the xorg.conf are (I tried a lot of different options):

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "XaaNoOffscreenPixmaps" "on"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "off"
        Option      "TexturedVideo" "on"
        Option      "TexturedXrender" "off"
        Option      "Textured2D" "on"
        Option      "UseFastTLS" "1"
        Option      "BackingStore" "on"
        BusID       "PCI:1:5:0"
        Option "TexturedVideoSync" "True"
        Option "MaxGARTSize" "128"
EndSection


Yes, I know, it is not very clear what happens... I am sorry, but I am little desperate, because it would work fine without this!

Thanks in advance!

---

### Post by phidia on 2008-08-15
There is a related thread [here]("http://ubuntuforums.org/showthread.php?t=769020&highlight=ati+x1200"). Try turning off all visual effects-I'm not sure exactly how to do that in KDE but it's probably in control center.

---

### Post by rogorido on 2008-08-15
thanks for your answer.

Yes, it is related to my problem. I think I saw this thread weeks ago. 

The problem is: if the effects are not enabled, the computer works very well. 

But, it seems to be a problem with DRI, DRI2, ati... a complicated issue...

maybe has anyone else another solution...

---

### Post by bigotefalso on 2008-08-20
Hi,

I have a Toshiba a215 s7422 laptop whit an ati radeon x1200 card. I have the same problem, it just crashes and there's an invisible (but visible) line!!

Rogorido:

If you deactivate compiz, then you'll fix that ******* line, but that's not a fair fix. But at least you cuold now see videos on youtube whitout issues. I recommend you to use compiz-fussion icon to turn off and on compiz in seconds.

En español:

Rogorido, yo creo que la cosa no es del xorg.conf, creo que es cosa de drivers. Te pido un gran favorsote: serias tan amable de decirme si wine y algun juego que requiera aceleracion 3D te corre bien? (desactivando compiz por supuesto)

Sabes por que creo que es cosa de drivers? por que he usado el catalyst 8.3, el catalyst 8.6 (por envy), y el 8.7, y con el 8.6 ni siquiera corrian los juegos en wine. Asi que regrese a 8.3 y ya corrio Warcraft 3 pero extremadamente lento. (El 8.7 me hace lo mismo que 8.3).

Estoy pensando seriamente en provar a ocupar drivers mas viejos, incluso provar los que emulaban la aceleracion 3D. (Mi ingles no es muy bueno)


In english:

Rogorido, I think that it is about drivers, not xorg.conf. I ask you one thing please: could you tell me if your wine runs well whit a game that requires 3D? (deactivating compiz of course)

You know why do I think that it is about drivers? Because I have used catalyst 8.3, 8.6 (through envy), and 8.7 (the newest). And 8.6 not even run games in wine, so I came back to 8.3 and it runs Warcraft 3 at least but extremely slow. (The 8.7 driver do the same as 8.3).

I'mm thinking seriously to try and older driver, even try those who emulate 3D aceleration. (My english is too bad).


Please, help us. There is a lot of guides who show us how to install correctly the drivers, and guides to configure the video card in my laptop, but no one says if wine runs well or that ******* line is going to kill us, or if we have to deactivate compiz to see videos.

If you have a radeon x1200, please, say if you can play games in wine without issues.

Thanks!

---

### Post by tuxxy on 2008-08-20
If its any help I know the x1250 should run compiz to some degree but not flawlessly like an nvidia card would

---

