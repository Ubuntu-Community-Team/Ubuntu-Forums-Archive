---
title: "Webcam HP"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by choujin7 on 2008-04-12
hi I'm new....first:excuse my bad english,I'm italian....I'm here 'cause it's one of the best ubuntu sites...:)
I've a notebook hp dv6000 series with gutsy 32...Are there any programs to manage my webcam?
I don't know where to looking for to try it...
please help me

---

### Post by linuxwizard on 2008-04-12
Go to Applications > internet > Ekiga Softphone >  See if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.



If cam does not work post the results of the command > lsusb

---

### Post by choujin7 on 2008-04-12
thank you....
if I click on the webcam icon,it outputs me this error.
Errore durante l'apertura del dispositivo video HP Webcam

Un logo animato sarà trasmesso durante le chiamate. Notare che è possibile trasmettere un'immagine data o il logo animato selezionando "Picture" come plugin video e "MovingLogo" o "StaticPicture" come periferica.

Il driver non supporta il formato video richiesto.

In few english words,there was an error with the opening of HP webcm,the driver doesn't work with this video type

:confused:

---

### Post by linuxwizard on 2008-04-12
Did you work with the settings ? Open Ekiga > Edit > Preferences > Video > Video Devices > change Video Plugin if it shows V4L change to V4L2 than try using cam again.

---

### Post by choujin7 on 2008-04-13
ah it was the plugin!
now it works very well....thank you so much,bye

---

### Post by linuxwizard on 2008-04-13
You're Welcome Glad to hear that you got your cam working. Please mark thread as SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

