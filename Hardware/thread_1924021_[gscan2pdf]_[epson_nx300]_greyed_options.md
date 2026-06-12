---
title: "[gscan2pdf] [epson nx300] greyed options"
date: 2012-02-11
forum: Hardware
---

### Post by parix on 2012-02-11
The scanner is connected to the computer through USB.
Ubuntu 11.10 updated.
epson nx300 (bx300f really, I think it's the same device, comercialized with different names)

A lot of the options appear grayed out, like brightness, but in Xsane it's available, so I guess it's not a SANE limitation.

[IMG]https://www.sugarsync.com/pf/D7717050_734_25019050?directDownload=true[/IMG]


[IMG]https://www.sugarsync.com/pf/D7717050_734_25019050[/IMG][IMG]https://www.sugarsync.com/pf/D7717050_734_25019066?directDownload=true[/IMG]

Any ideas? Thanks!

---

### Post by tea for one on 2012-02-12
Good morning

I do not have an Epson device but I came across this little snippet of information via the recent Tuxradar podcast.

There is a download area for Linux drivers on the Epson website

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Even if this information is not the exact solution for this problem, it may help in the future.

---

### Post by parix on 2012-02-12
Good evening! Thanks a lot for the suggestion,

I followed the links you suggested and downloaded [COLOR=Blue]*[the proprietary software from Epson]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16703&DSCCHK=58a02a45102a78499d417177b4b4117403a4c878")* [/COLOR], a very recent version, and although it still uses SANE at the back of the back-end, it creates a new device  entry.

I chose the **iscan_2.28.1-3.ltdl7_i386.deb** because it's says*[COLOR=Blue] [here]("http://ubuntuforums.org/archive/index.php/t-1266259.html")[/COLOR] * that the ltdl7 version is needed (though I still don´t know what ltdl7 means it sounds to me as limited and download)

Also the **iscan-data_1.14.0-1_all.deb** is needed as a dependency. I guess it by itself creates the new "device" entry.

The iscan standalone app works no better than Xsane, because although you can control Brightness and Contrast you cant interpolate even and odd pages for 2 sided documents as gscan2pdf lets you do..



That new entry still shows some greyed out option, but crucially I can now control Brightness and Contrast and that's all I wanted.  :popcorn:

(in the picture it is selected in the libsane-perl frontend, as shown in gscan2pdf).

[IMG]http://ubuntuone.com/1ZkgQ26NDvufT8s4i5psMp[/IMG]

---

### Post by tea for one on 2012-02-12
Splendid, I'm pleased that the information provided a partial result.

I admit that I'm now officially out of my depth and hopefully somebody else can step in and offer more fruitful suggestions.

Kind regards

---

