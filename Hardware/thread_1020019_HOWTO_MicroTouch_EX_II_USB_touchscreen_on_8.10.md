---
title: "HOWTO: MicroTouch EX II USB touchscreen on 8.10"
date: 2008-12-23
forum: Hardware
---

### Post by naeb on 2008-12-23
Here's how I got a MicroTouch EX II touchscreen working under Intrepid (using fdi policy instead of xorg.conf).


Step 1:  Get the evtouch driver
```
sudo apt-get install xserver-xorg-input-evtouch
```
Make sure the universe repository is enabled.
 

Step 2:  Use lshal to find the touchscreen (*it needs to be plugged in*)
```
lshal | less
```
You'll probably find multiple entries corresponding to the touchscreen.  The one of interest contains "input" statements (e.g. info.category = 'input',  linux.subsystem = 'input')
Make note of a unique key from that section (I used input.product)


Step 3:  Create the file /etc/hal/fdi/policy/touchscreen.fdi containing:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
                <match key="input.product" contains="MicroTouch Systems, Inc. MicroTouch USB Touchscreen - EX II">
                        <merge key="input.x11_driver" type="string">evtouch</merge>
                        <merge key="input.x11_options.MinX" type="string">14200</merge>
                        <merge key="input.x11_options.MaxX" type="string">2160</merge>
                        <merge key="input.x11_options.MinY" type="string">2580</merge>
                        <merge key="input.x11_options.MaxY" type="string">13800</merge>
                </match>
        </device>
</deviceinfo>

```
Notice the "<match key=" statement contains the value obtained in Step 2.


Step 4:  Unplug and plug back in the touchscreen.  It should now work, no need to restart X!  


Note: After installing evtouch, "System->Administration->Calibrate Touchscreen" appears.  Using this tool (at least for this particular chipset) results in an inverted X-axis.  Don't touch it.

---

### Post by cacycleworks on 2010-06-29
UPDATE (to help anyone Google-ing for this same problem):

Note that as installed with 10.04 or 9.04 without modification, the touchscreen behaves correctly, save for the x-axis is inverted. Sadly, nothing I tried in 10.04 would work. The latest drivers just don't recognize the swapx option. :( [I did file a bug report]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/598331").

After several hours of failing to get my touchscreen to behave correctly in Ubuntu 10.04, here is my recipe that worked.

Ubuntu 9.04 amd64 installed on hardware:
- [Acer Aspire R1600 mini pc]("http://support.acer.com/acerpanam/desktop/2009/Acer/aspire/AspireR1600/AR1600nv.shtml") with intel Atom 230 CPU (64 bit)
- Dell E153FPT / E153FPTc 15" touchscreen monitor from POS system. Has Microtouch EXII USB controller
- AT&T USB 3G usb stick
- Dell USB [mag card swipe reader]("http://accessories.us.dell.com/sna/products/retail_pos_accessories/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=a0062719"), $59

```
sudo apt-get install xserver-xorg-input-evtouch
```
Then edit /usr/share/hal/fdi/policy/20thirdparty/50-touchkit.fdi
to this:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Touchscreen">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">1083</merge>
        <merge key="input.x11_options.miny" type="string">1348</merge>
        <merge key="input.x11_options.maxx" type="string">15624</merge>
        <merge key="input.x11_options.maxy" type="string">15700</merge>
        <merge key="input.x11_options.swapx" type="string">1</merge>
    </match>
  </device>
</deviceinfo>

```

Note that this fdi file is a work in progress and I'm continually tweaking the options to get the touch more perfect. If you go down this route, I suggest doing a sudo chmod 666 to 50-touchkit.fdi, so you can edit it upon logging in without having to sudo each time. Note that you must restart the computer for the changes to take effect. Logging out / restarting X doesn't reflect the changes I made.

The 3G usb stick works without any mods or hassle. Just pick the carrier, put in the phone number, and leave all other fields blank. This setup is our mobile POS solution. We are normally an e-commerce business, so there's no advantage for us to get a portable swiper, as our account is all for keyed in rates. If we had more consistent card-present transactions, then it would be prudent to purchase a proper card swipe terminal. As it is, this solution was put together entirely from unused spare hardware on hand.

Yaay

---

### Post by vbundi on 2010-07-29
> **cacycleworks said:**
> UPDATE (to help anyone Google-ing for this same problem):

Note that as installed with 10.04 or 9.04 without modification, the touchscreen behaves correctly, save for the x-axis is inverted. Sadly, nothing I tried in 10.04 would work. The latest drivers just don't recognize the swapx option. :( [I did file a bug report]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/598331").

After several hours of failing to get my touchscreen to behave correctly in Ubuntu 10.04, here is my recipe that worked.

Ubuntu 9.04 amd64 installed on hardware:
- [Acer Aspire R1600 mini pc]("http://support.acer.com/acerpanam/desktop/2009/Acer/aspire/AspireR1600/AR1600nv.shtml") with intel Atom 230 CPU (64 bit)
- Dell E153FPT / E153FPTc 15" touchscreen monitor from POS system. Has Microtouch EXII USB controller
- AT&T USB 3G usb stick
- Dell USB [mag card swipe reader]("http://accessories.us.dell.com/sna/products/retail_pos_accessories/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=a0062719"), $59

```
sudo apt-get install xserver-xorg-input-evtouch
```
Then edit /usr/share/hal/fdi/policy/20thirdparty/50-touchkit.fdi
to this:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Touchscreen">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">1083</merge>
        <merge key="input.x11_options.miny" type="string">1348</merge>
        <merge key="input.x11_options.maxx" type="string">15624</merge>
        <merge key="input.x11_options.maxy" type="string">15700</merge>
        <merge key="input.x11_options.swapx" type="string">1</merge>
    </match>
  </device>
</deviceinfo>

```

Note that this fdi file is a work in progress and I'm continually tweaking the options to get the touch more perfect. If you go down this route, I suggest doing a sudo chmod 666 to 50-touchkit.fdi, so you can edit it upon logging in without having to sudo each time. Note that you must restart the computer for the changes to take effect. Logging out / restarting X doesn't reflect the changes I made.

The 3G usb stick works without any mods or hassle. Just pick the carrier, put in the phone number, and leave all other fields blank. This setup is our mobile POS solution. We are normally an e-commerce business, so there's no advantage for us to get a portable swiper, as our account is all for keyed in rates. If we had more consistent card-present transactions, then it would be prudent to purchase a proper card swipe terminal. As it is, this solution was put together entirely from unused spare hardware on hand.

Yaay

I've followed these instructions, but when I touch my screen, the pointer dissapears (offscreen?). When I move my regular mouse, the cursor moves back into the screen area.


I'm using a dell E153FPTc 15".

---

### Post by cacycleworks on 2010-07-29
> **vbundi said:**
> I've followed these instructions, but when I touch my screen, the pointer dissapears (offscreen?). When I move my regular mouse, the cursor moves back into the screen area.

I'm using a dell E153FPTc 15".

Probably the X and Y numbers need tweaking. Remember that the origin is top left (I think) and then the size of the numbers determine where the values start and stop. Mucking about with a calibrate utility in 9.04 seemed to help me somewhat.

We just did our trade show this weekend and our POS solution worked fantastically.

---

### Post by vbundi on 2010-07-30
Hey, thanks for the reply.

By default Lucid uses usbtouchscreen module.  And it works well other than that the min/maxs need to be tweaked a bit and the X needs to be swapped.

After installing evtouch, it doesn't work at all, even with this hw profile you've made up.

You say that you had a calibration utility in 9.04?  What was it called?

I'm connecting my screen with usb, there is no serial on this thing, if that makes any difference.  I tried touchcal 0.31, and it would crash every time, maybe because I wasn't using it right.

Any suggestions would be great.

---

### Post by cacycleworks on 2010-07-30
type calibrate into the command line and hit tab 2 or 3 times to see all of the executables ... that or try "touch" and tab-tab to see the names of executables in your path.

Unfortunately, that computer isn't currently set up, but if it comes to it, there is a workstation I can swap it into to try and figure out what I did to it.

---

