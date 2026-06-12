---
title: "Webcam widget"
date: 2008-10-07
forum: General Help
---

### Post by legolasfaol on 2008-10-07
Some months ago, someone asked if there was a widget to monitor a webcam on his desktop.
Well, up to now there isn't, but I think there is a usefull trick:
This trick consists into:
- create a folder into your home folder (eg. wallpaper)
- create a crontab that downloads the images of a webcam
```
- from terminal: "sudo crontab -e"
- paste "*/5 * * * * wget http://*URLOFTHEWEBCAM*.jpg -O /home/*user*/wallpaper/webcam.jpg"
- save and exit
``` (*/5 indicates that it would be downloaded every 5 minutes)
- install kdeplasma-addons: "sudo apt-get install kdeplasma-addons"
- add "picture frame" widget on your desktop and configure it to pic images from the "wallpaper" folder

Of course you can add a new line to "crontab -e" with a new address to add a new webcam

For any problems, add here your questions

P.S. you can use the same technique to view webcams on your wallpaper with the "slideshow" option, but if you use just 1 webcam it doesn't update the image. You should use at least 2 webcams or duplicate the webcam image in his folder (just add IN THE SAME LINE" && cp /home/*user*/webcam/webcam.jpg /home/*user*/webcam/webcam2.jpg" to the crontab command, I repeat DON'T START A NEW PARAGRAPH!

---

### Post by flameup on 2008-10-07
So to realize that Crontab is needed? Be aware most shared hosts do not support that ;)

---

### Post by legolasfaol on 2008-10-07
yes, unfortunatly up to now I think that this is the only solution

---

