---
title: "printer drivers"
date: 2012-05-31
forum: Hardware
---

### Post by StrangerSa on 2012-05-31
Hi Guys

I found printer drivers for linux for my printer /fax Canon Pixma mx 350

I have downloaded them but have no idea how to make them work in Ubuntu

can you please assist ?

There are all tar.gz format

---

### Post by eklikeroomys on 2012-05-31
If you're lucky and your printer is supported, you shouldn't have to manually download drivers for your printer.

Connect the printer to your PC, then press the super (windows) key, and type printing. A printing icon should appear, click on it.

On the window that appears, click on add and follow the instructions for installing your printer. Somewhere along the line, you will be asked for your printer's make and model, which will allow the drivers to be downloaded automatically.

Hope this helps! :popcorn:

Regards,
eklikeroomys

---

### Post by philinux on 2012-05-31
> **StrangerSa said:**
> Hi Guys

I found printer drivers for linux for my printer /fax Canon Pixma mx 350

I have downloaded them but have no idea how to make them work in Ubuntu

can you please assist ?

There are all tar.gz format

You printer is not listed in Printing as mentioned in post 2. the 340 and 360 are. From Canon the printer driver is this one [http://support-au.canon.com.au/contents/AU/EN/0100272202.html](http://support-au.canon.com.au/contents/AU/EN/0100272202.html) and for scanning [http://support-au.canon.com.au/contents/AU/EN/0100272902.html](http://support-au.canon.com.au/contents/AU/EN/0100272902.html)

Download these and then for the first one right click and choose extract here. Open the extracted folder and double click on the install.sh file.

Do the same for the scanner tar file.

---

### Post by deadflowr on 2012-05-31
If philinux's suggestion doesn't work. Inside the extracted folder is a folder called packages. open that and inside are deb files. One will say common-something-something, and the other your printer name. double-click, or right click the common-whatever first to open the ubuntu software center to install it, and then repeat that with printer one. You have to install the common deb first.
When your done, open printers and then add printer(If your going to run it wirelessly, click on network printer and hopefully something like cjinet-something-something will appear. that will be your printer, choose it and follow the steps, test print and you should be good to go.

---

### Post by StrangerSa on 2012-06-01
Thanks all will try those options now. I did try the add printer and the 350 is not on the list, so thanks for spotting that and giving the other solutions to try.

Cheers

---

