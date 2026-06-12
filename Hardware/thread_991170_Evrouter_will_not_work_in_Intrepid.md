---
title: "Evrouter will not work in Intrepid"
date: 2008-11-23
forum: Hardware
---

### Post by pennstatebadboy on 2008-11-23
Ever since I did the Intrepid upgrade, Evrouter hasn't been working for me. I use it to enable buttons on my Gyration Media Center "air mouse"/remote control. 

Does anyone know why it's not working? It's really getting annoying. Thanks.

---

### Post by pennstatebadboy on 2008-11-23
Xbindkeys isn't working either. Is there something going on with the mapping in Intrepid that's different than previous versions of Unbuntu?

---

### Post by pennstatebadboy on 2008-11-25
bump

---

### Post by prensing on 2009-08-17
I just got a Gyration remote. Originally, I thought it was partially working, but it turned out that Ubuntu (9.04) was picking up the keys which map onto a normal keyboard.

From various web sites, I discovered that X11 is grabbing the event buffers so neither evrouter nor lirc work properly. 

You can turn off hal support for it by adding a rule. Edit the file /usr/share/hal/fdi/preprobe/20thirdparty/gyration.fdi with the content:
```
 <?xml version="1.0" encoding="UTF-8"?>

 <deviceinfo version="0.2">
  <device>
     <match key="usb.vendor_id" int="3094">
       <match key="usb.interface.number" int="0">
         <merge key="info.ignore" type="bool">true</merge>
       </match>
     </match>
  </device>
 </deviceinfo>

``` Note that this is more complicated than other rules I saw on the Web. It only blocks hal from handling the keyboard part of the remote, leaving the mouse handling intact.

Then, follow directions such as [here]("http://www.mythtv.org/wiki/Gyration-based_MCE_Remotes") to set up LIRC.

---

### Post by williammanda on 2009-09-05
> **prensing said:**
> Here is a better HAL rule which preserves the mouse functionality.

Use this as the match:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="usb.vendor_id" int="3094">
       <match key="usb.interface.number" int="0">
         <merge key="info.ignore" type="bool">true</merge>
       </match>
     </match>
  </device>
</deviceinfo>
```

I put it in the file /usr/share/hal/fdi/preprobe/20thirdparty/gyration.fdi.

This blocks HAL from handling just the 1st interface which is the keyboard. 

Be warned that this might block other Gyration products, so you might have to experiment some more if you have more than just a remote.

Well after waiting six months for things to evolve I took another look at getting the gyration remote working. I decided to try the fix that prensing presented. I tried this on two different computers. The first one, I followed prensing's advice and the remote worked as expected. I had the functionality of the mouse as well as the mythtv functions.
The second computer I installed the changes except for prensing's fdi change and everything again worked as expected. One changed from the previous install was that I re-installed ubuntu 9.04 on the second computer. At this time I can't validate prensing's change. In addition I went ahead and made prensing's change to the 2nd computer (after the remote was working as expected) and it made no difference.
When I setup lirc through Mythbuntu control center I selected custom as the remote. The lirc.fdi was created:

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-Receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="cx88 IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="bttv IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="Budget-CI dvb ir receiver saa7146">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>


So at this time can't validate anything being done to hal makes a difference.
Thanks

---

