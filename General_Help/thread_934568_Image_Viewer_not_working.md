---
title: "Image Viewer not working"
date: 2008-09-30
forum: General Help
---

### Post by Prominence on 2008-09-30
I double click the image, and nothing happens, why?

---

### Post by AllanPoe on 2008-09-30
What are the options of the "open with" submenu if you click on the image with a right-click? Is image Viewer there?
What kind of image is it? jpg, png, ...?

---

### Post by Prominence on 2008-09-30
I right click, click the option "Open with Image Viewer" and in the submenu it offers to open with Firefox, GIMP, and Thunderbird.

---

### Post by ThaddeusW on 2008-09-30
> **Prominence said:**
> I double click the image, and nothing happens, why?

Well there is the possibility you dont have that images mime type set. Right click on it and try "open with" and see if there are any alternative applications you can use. If not it will allow you to pick one and depending on your desktop environment type either konqueror for KDE or nautilus for Gnome. There you should also be able to set that application as the default viewer. 

Another reason is you might not be able to open the image format if its not a standard like png or jpg. More information is needed.

---

### Post by AllanPoe on 2008-09-30
> **Prominence said:**
> I right click, click the option "Open with Image Viewer" and in the submenu it offers to open with Firefox, GIMP, and Thunderbird.

So, can you open the image with GIMP?

---

### Post by Prominence on 2008-09-30
Yeah, it opens with everything else perfectly. There's no other opinion but those three, so I don't know what to do, and it's a pain to start up Picasa to view images.

---

### Post by kaibob on 2008-09-30
While in Nautilus, right-click on an image file and select "open with" and then "open with other application...." You can then select one of the applications shown or the "Use a custom command" option. If you use the latter, enter eog for Eye of Gnome.

---

### Post by Prominence on 2008-09-30
What's the thing for the eye of gnome?

---

### Post by karlr42 on 2008-09-30
it's eog, which is the default image viewer.
Try ```

cd /path/to/picture
eog image.jpg
```
or whatever the filename is

---

### Post by Prominence on 2008-09-30
Man...I'm completely lost.

---

### Post by kaibob on 2008-09-30
> **Prominence said:**
> Man...I'm completely lost.

1) Load Nautilus.

2) Navigate to a folder that contains an image file and right-click on that image file.

3) Select "Open with".

4) Select "Open with other application...."

5) Click on the arrow next to "Use a custom command."

6) In the text area, enter "eog" (omit quotes).

7) Click on the "Open" button.

The image file should open in Eye of Gnome, which is the default image viewer. If nothing happens, you should open synaptic and do a search to make sure that eog is installed. If it is, then there is some other problem, and I don't know what that is.

---

### Post by Prominence on 2008-10-01
Still nothing.

---

### Post by AllanPoe on 2008-10-01
Check if eog package is installed in synaptic. If not, install it. If yes, remove it and then install it again. Or, alternatively, you can install another Image Viewer - [http://linuxappfinder.com/graphics/imageviewers](http://linuxappfinder.com/graphics/imageviewers)

---

### Post by Prominence on 2008-10-01
yeah...not working, which do you suggest?

---

### Post by AllanPoe on 2008-10-01
You could try [http://linuxappfinder.com/package/imview](http://linuxappfinder.com/package/imview).
There is a hardy package at the bottom of the page.

---

### Post by kaibob on 2008-10-02
> **Prominence said:**
> Still nothing.

The best way to troubleshoot this is to open a terminal window and enter:

```
eog
```

An application called "Eye of Gnome Image Viewer" should load. If it doesn't, something is wrong with the install of this program. If it does load, go back to my above instructions.

---

### Post by Prominence on 2008-10-02
I ran that and it came up, but I got Gthumbs or whatever it is, and it's even better.

---

### Post by kaibob on 2008-10-02
> **Prominence said:**
> I ran that and it came up, but I got Gthumbs or whatever it is, and it's even better.

So, your issue is resolved?

---

### Post by Prominence on 2008-10-03
yep

---

