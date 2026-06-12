---
title: "How to enable secondary display (not twinview)"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by rob_bigdog on 2007-06-03
Here's my setup:
My PC's in my bedroom.  On the other side of the wall is the living room.

I'm using an AGP NVIDIA GeForce 5200; it has dual-monitor support.  The DVI monitor port (the primary one, apparently) is connected through the wall to my DLP HDTV (the SPDIF output also goes through the wall to my receiver - it's a really nice setup).  The analog port connects to a Sceptre X9G LCD (for reference: [http://www.newegg.com/Product/Product.aspx?Item=N82E16824112177](http://www.newegg.com/Product/Product.aspx?Item=N82E16824112177)) in my bedroom.

When I enabled the NVIDIA proprietary driver, the screen went blank.  I'm a noob so it took a little while, but I figured out (from the xorg.conf file) that the DLP is setup as the primary display.  That's why my screen went blank - I'm in the bedrrom looking at my LCD.

What I'd like to do is this: setup the configuration such that the LCD is the only active display.  I've actually tried (with no luck) to setup the system for Twinview, but to no avail.  I never use the PC as a media center anymore (since I got the PS3 - it's media center functions work just fine for me), and I don't want to risk sending an unsupported signal to the DLP (the user guide warns explicitly about this).

I'm using Feisty - installed earlier this weekend.  It's currently using the installer-generated xorg.conf file (which only mentions the DLP in the monitor section); I backed it up and restored it when Twinview didn't work out.

Any help will be greatly appreciated!

---

### Post by Bohlio on 2007-06-03
Im sorry that I'm not any help, but I'd like to comment that you have a super awsome setup! :-)
<Bump> ;)

---

