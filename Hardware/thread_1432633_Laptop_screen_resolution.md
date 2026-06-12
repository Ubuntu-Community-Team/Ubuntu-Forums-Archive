---
title: "Laptop screen resolution"
date: 2010-03-18
forum: Hardware
---

### Post by rodhash on 2010-03-18
Hello,

How do I know what's the available screen resolution for a specific laptop?

The laptop specification says:

"... 14.1" diagonal WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)..."

However I'm using another laptop model / manufacturer, also with a 14.1" screen, and my resolution it's 1440x900.

Thanks.

---

### Post by devildoc5 on 2010-03-18
the best bet would be to check out the manufacturer's website (HP in this case)  If that turns up nothing you can always look in the manual that came with the laptop...You know the one that is holding up your coffee table?

---

### Post by norseman-has-a-laptop on 2010-03-18
you can also benchmark your laptop and find out that way if you want to let a program do it for you

---

### Post by rodhash on 2010-03-18
Actually I'd like to know if this screen (14.1") will be able to work with the resolution 1440x900.

I have another laptop (15.4") that does not work with 1440x900 resolution :-(

At least I couldn't set this resolution yet.

---

### Post by Goveynetcom on 2010-03-18
> **rodhash said:**
> Actually I'd like to know if this screen (14.1") will be able to work with the resolution 1440x900.

I have another laptop (15.4") that does not work with 1440x900 resolution :-(

At least I couldn't set this resolution yet.
I have an HD monitor on my laptop, it doesn't display fully at the right resolution, and I can't really change it.

It's close enough, so I have to stick with it. I think the options are locked so you don't accidentally set the range outside of your monitor's range.

---

### Post by norseman-has-a-laptop on 2010-03-18
> **Goveynetcom said:**
> I have an HD monitor on my laptop, it doesn't display fully at the right resolution, and I can't really change it.

It's close enough, so I have to stick with it. I think the options are locked so you don't accidentally set the range outside of your monitor's range.
that sounds to be about right ....still benchmarking you systems always a good idea

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> that sounds to be about right ....still benchmarking you systems always a good idea
lol, IDK what that means...

Makes me feel stupid...

Maybe I should pay more attention during my Computer Maintenance class :D...

I assume it is quite helpful...

---

### Post by norseman-has-a-laptop on 2010-03-18
ah its just like stress testing but with results and stuff
if its in your comp its will be tested 
go searching for a good computer benchmarker lol

---

### Post by rodhash on 2010-03-18
Does somebody know why the maximum resolution is 1280x800 for this 15.4" screen?

---

### Post by era86 on 2010-03-18
There is a difference between WXGA and WXGA+ models of LCDs.  You can read the differences here: [http://en.wikipedia.org/wiki/WSXGA_Wide_XGA%2B](http://en.wikipedia.org/wiki/WSXGA_Wide_XGA%2B)

Essentially, the WXGA+ has more pixel real estate so you can fit more on the screen.  It will, however, make text smaller and such.  If you are trying to do a panel swap, you'll want to make sure the panel is the SAME resolution as your current panel in your laptop.  There are SOME laptops that allow a resolution upgrade, see my blog in the sig. :)

What are you trying to do?

Edit: By the way, WXGA is usually 1280x800 and WXGA+ is 1440x900 on 14.1" laptops.  In later 15" laptops, the 16:9 ratio is becoming standard so WXGA+ on 15" is 1600x900 I believe.  May want to double check me.

---

### Post by rodhash on 2010-03-18
Hi,

I believe there's something weird.

For the lenovo laptop it says WXGA and for the HP as well.

-> Lenovo:
[http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400](http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400)

-> HP:
[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Ultra-Portable&series_name=dv4i_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Ultra-Portable/dv4i_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Ultra-Portable&series_name=dv4i_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Ultra-Portable/dv4i_series)


However I'm using this lenovo laptop, and my resolution is currently 1440x900 as we can see below:

rodhash@gnurodhash:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   59.9     50.0


I'm wondering if this HP laptop also support the 1440x900 resolution.

Any idea ?

Thanks.

---

### Post by era86 on 2010-03-18
> **rodhash said:**
> Hi,

I believe there's something weird.

For the lenovo laptop it says WXGA and for the HP as well.

-> Lenovo:
[http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400](http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400)

-> HP:
[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Ultra-Portable&series_name=dv4i_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Ultra-Portable/dv4i_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Ultra-Portable&series_name=dv4i_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Ultra-Portable/dv4i_series)


However I'm using this lenovo laptop, and my resolution is currently 1440x900 as we can see below:

rodhash@gnurodhash:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   59.9     50.0


I'm wondering if this HP laptop also support the 1440x900 resolution.

Any idea ?

Thanks.

For he T400, there is an option to get WXGA+.  You have WXGA+ if you are viewing at 1440x900 on a 14.1" laptop.  If the HP has WXGA, then it will be displaying 1280x800.  Unless you find a WXGA+ option on it, that's what the resolution will max at.

---

### Post by rodhash on 2010-03-19
Oh yeah, that's right.

Thanks for the clarification.

Unfortunately none of the HP laptops with 14.1" screen supports 1440x900 resolution :-(

I wanted to buy a HP laptop, but I really would like to work with this screen size and resolution.

Another question. For a WSXGA+ screen (1680x1050) it's possible to set 1440x900 ?

---

### Post by era86 on 2010-03-19
I don't know if you can find WSXGA+ screens anymore.  The industry is making the 16:9 ratio a standard.

But to answer your questions, you should be able to set the resolution to UP TO 1680x1050.  Also, since their ratios are the same (16:10), it should look semi-decent.

---

### Post by norseman-has-a-laptop on 2010-03-19
> **era86 said:**
> I don't know if you can find WSXGA+ screens anymore.  The industry is making the 16:9 ratio a standard.

But to answer your questions, you should be able to set the resolution to UP TO 1680x1050.  Also, since their ratios are the same (16:10), it should look semi-decent.
yummy

---

### Post by rodhash on 2010-03-19
I found some laptop with  1600 x 900, now I'm wondering if it works with 1440x900 (doubt)

---

### Post by rodhash on 2010-03-19
I mean, I'm wondering if it will display fine if I set 1440x900 instead of 1600x900. And also if it's possible.

---

### Post by era86 on 2010-03-20
> **rodhash said:**
> I mean, I'm wondering if it will display fine if I set 1440x900 instead of 1600x900. And also if it's possible.

You would be trying to display 16:10 resolution in a 16:9 screen.  Don't think it will look too pretty.  I don't even think you will be able to select it.

---

### Post by rodhash on 2010-03-20
To get the best image quality should I set the maximum resolution?

---

