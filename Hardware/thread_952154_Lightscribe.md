---
title: "Lightscribe?"
date: 2008-10-18
forum: Hardware
---

### Post by Prominence on 2008-10-18
My laptop came with lightscribe and I was wondering if there was a way to use it under linux.

---

### Post by fballem on 2008-10-18
> **Prominence said:**
> My laptop came with lightscribe and I was wondering if there was a way to use it under linux.

Go to [http://www.lightscribe.com](http://www.lightscribe.com). Once you are there, select Downloads, then Linux. You will have a screen similar to LightScribe Download screenshot (attached).

Download both the system software and the simple labeler (select the .deb versions). Save them to the Desktop.

Install the system software first by double clicking on it. This will open up the debian package installer. Click install.

Install the simple labeler second by double clicking on it. This will open up the debian package installer. Click install.

Once both are installed, then right-click on the Applications menu in the top panel and select Edit Menus. This will open up a dialog similar to Edit Menu screenshot. 

Click on 'Other' from the list, then select New Item. You will have a screen similar to Screenshot-Create Launcher (attached). Set up the values similar to what I have shown. In addition, if you click on the icon on the left side, you can specify the icon. You can browse to /opt/lightScribeapplications/SimpleLabeler/content/images. Once there, you can select an image to use for the icon.

Once done, click OK and you should be good to go.

You may choose to have a higher contrast label by opening a terminal and copying the following code into it:

```
sudo /usr/lib/lightscribe/elcu.sh
```

You will be asked to enter your password. A small menu will show, select option 1.

Hope this helps,

---

