---
title: "Multi-Touch Scrolling on eee 1201N"
date: 2010-03-10
forum: Hardware
---

### Post by capleton on 2010-03-10
**SOLVED**.   Check my third post for the tutorial.

---

### Post by capleton on 2010-03-11
bump

---

### Post by capleton on 2010-03-11
Well I did a lot of research and finally got it working.  Here's a little tutorial for those who might be interested.

**First**, you need SHMConfig enabled.  (see [here.]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig"))  As the tutorial says, first run the following.  (In my case i used mousepad instead of gedit because I use xfce)```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

``` 

Then put this into the file:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```

**Second** you need to test the touchpad to see if it actually recognizes multiple fingers.  You do this by running ```
synclient -m 250
```  (that last number is the amount of milliseconds it takes to refresh)  Use ctl-c to stop.  anyway, the output will be lines and lines of this ```
~ $ synclient -m 250
 216.975     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
 213.969  2061 3543  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
 214.224  2240 3185  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
 214.474     1 5855   2 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 214.724     1 5855   3 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 214.974  2076 2813  57 1 11  0 0 0 0 0  00000000   0  0  0   0   0
 215.225  2254 2482  63 1 13  0 0 0 0 0  00000000   0  0  0   0   0
 215.475  2271 2896  63 1 12  0 0 0 0 0  00000000   0  0  0   0   0
 215.725  2144 2593  63 1 13  0 0 0 0 0  00000000   0  0  0   0   0
 215.975  2325 2551  63 1 14  0 0 0 0 0  00000000   0  0  0   0   0
 216.225  2261 2787  63 1 14  0 0 0 0 0  00000000   0  0  0   0   0
 216.475  1854 2738  63 1 12  0 0 0 0 0  00000000   0  0  0   0   0
 216.725     1 5855   1 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 216.975     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

```  

Now comes time to analyze the data.  (This is thanks to jnjackin at ucalgary [here]("http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html").  So under "**f**" you will see either a 0, 1, or 2 as it monitors what you do with the touchpad.  If it only reads 0 or 1, that means that the touchpad is not recognizing multiple fingers. If it reads a 2, that means that it does, and you're probably not reading this thread.  Anyway, so if it doesn't read a 2, this means we will have to emulate the two-finger scrolling.

**Third** you need to emulate a two-finger press by using both the depth (z) and width (w) differences between one finger and two. And you must set these values by changing variables called EmulateTwoFingerMinZ and EmulateTwoFingerMinW. This is where I ran into problems because the file that holds these values was in two different directories for me:

/etc/hal/fdi/policy/11-x11-synaptics.fdi     and
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

They both have the same name, however, the file that is in /etc/hal... seems to be the one that actually made a difference for me.  If you don't have this file in this location, use the other.  And always remember to create a backup the file before altering it.  Okay, now here's what I did (i will use gedit to be consistent, i actually used mousepad bc im in xfce) ```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi

``` And then I added the following so that it finally looked like this
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">40</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>*
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">3</merge>
       <merge key="input.x11_options.TapButton3" type="string">2</merge>
   </match>
 </device>
</deviceinfo>

```
**BUT** your values may vary from what is above. And you must judge your values from the output of synclient. (from jnjackin's page)> ...pay attention to the 'z' (pressure) and 'w' (width) values. In my case, w is between 3-5 when one finger is touching, and above 7 when two fingers are touching. Thus, I set EmulateTwoFingerMinW (in 11-x11-synaptics.fdi - see the steps in the section above) to 7, so that synaptics will report two fingers when w is 7 or above. In my case, z isn't so directly related to the number of fingers touching, and I just picked a value that z is always above when two fingers are touching. As with w, set EmulateTwoFingerMinZ to this value.  

There.  Phew.  Three agonizing steps that I finally figured out after hours of searching.  Hope this helps at least someone.  If you have any questions, feel free to post on this thread.

---

### Post by widebluecraig on 2010-03-22
Many thanks Capleton!

I followed all steps - when using synclient 'w' never moved from zero. Of the two only 'z' was active.

I backed up and replaced my different looking /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi with yours. With only the following changes:

 ```
<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
 <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">0</merge>*  
```

/etc/hal/fdi/policy/11-x11-synaptics.fdi did not exist.

both vertical and horizontal two finger scrolling are working.

Thanks again for a great tuturial :)

---

### Post by capleton on 2010-03-22
:guitar:

---

### Post by Manslen on 2010-03-26
Is the sample output you posted the one you've actually used? It has "w" contantly at 0. Incidentally, that's similar to the output I'm getting, and I am unable to emulate the two finger scroll.

---

### Post by capleton on 2010-03-30
> **Manslen said:**
> Is the sample output you posted the one you've actually used? It has "w" contantly at 0. Incidentally, that's similar to the output I'm getting, and I am unable to emulate the two finger scroll.

I just updated my tutorial to include a sample of my own synclient output.  Anyway, yes if yours is similar to what had been posted previously, with "w" constantly at 0, then it would appear that your touchpad does not detect the width of the touches.  Therefore you would have to rely only the changes in the "Z" ouput to enable the two-finger scrolling.  Therefore if there are drastic differences between your "z" ouput with one finger vs your "z" ouput with two fingers, you could still enable two-finger scrolling.  Let me know if you manage to get it working :)

---

### Post by thelastblack on 2010-08-19
> **capleton said:**
> Well I did a lot of research and finally got it working.  Here's a little tutorial for those who might be interested.

**First**, you need SHMConfig enabled.  (see [here.]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig"))  As the tutorial says, first run the following.  (In my case i used mousepad instead of gedit because I use xfce)```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

``` 

Then put this into the file:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```

**Second** you need to test the touchpad to see if it actually recognizes multiple fingers.  You do this by running ```
synclient -m 250
```  (that last number is the amount of milliseconds it takes to refresh)  Use ctl-c to stop.  anyway, the output will be lines and lines of this ```
~ $ synclient -m 250
 216.975     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
 213.969  2061 3543  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
 214.224  2240 3185  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
 214.474     1 5855   2 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 214.724     1 5855   3 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 214.974  2076 2813  57 1 11  0 0 0 0 0  00000000   0  0  0   0   0
 215.225  2254 2482  63 1 13  0 0 0 0 0  00000000   0  0  0   0   0
 215.475  2271 2896  63 1 12  0 0 0 0 0  00000000   0  0  0   0   0
 215.725  2144 2593  63 1 13  0 0 0 0 0  00000000   0  0  0   0   0
 215.975  2325 2551  63 1 14  0 0 0 0 0  00000000   0  0  0   0   0
 216.225  2261 2787  63 1 14  0 0 0 0 0  00000000   0  0  0   0   0
 216.475  1854 2738  63 1 12  0 0 0 0 0  00000000   0  0  0   0   0
 216.725     1 5855   1 1  5  0 0 0 0 0  00000000   0  0  0   0   0
 216.975     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

```  

Now comes time to analyze the data.  (This is thanks to jnjackin at ucalgary [here]("http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html").  So under "**f**" you will see either a 0, 1, or 2 as it monitors what you do with the touchpad.  If it only reads 0 or 1, that means that the touchpad is not recognizing multiple fingers. If it reads a 2, that means that it does, and you're probably not reading this thread.  Anyway, so if it doesn't read a 2, this means we will have to emulate the two-finger scrolling.

**Third** you need to emulate a two-finger press by using both the depth (z) and width (w) differences between one finger and two. And you must set these values by changing variables called EmulateTwoFingerMinZ and EmulateTwoFingerMinW. This is where I ran into problems because the file that holds these values was in two different directories for me:

/etc/hal/fdi/policy/11-x11-synaptics.fdi     and
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

They both have the same name, however, the file that is in /etc/hal... seems to be the one that actually made a difference for me.  If you don't have this file in this location, use the other.  And always remember to create a backup the file before altering it.  Okay, now here's what I did (i will use gedit to be consistent, i actually used mousepad bc im in xfce) ```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi

``` And then I added the following so that it finally looked like this
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">40</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>*
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">3</merge>
       <merge key="input.x11_options.TapButton3" type="string">2</merge>
   </match>
 </device>
</deviceinfo>

```
**BUT** your values may vary from what is above. And you must judge your values from the output of synclient. (from jnjackin's page)  

There.  Phew.  Three agonizing steps that I finally figured out after hours of searching.  Hope this helps at least someone.  If you have any questions, feel free to post on this thread.

hi
i did all of these but when i use:
**synclient-m 250 **
it say:
**Can't access shared memory area. SHMConfig disabled?**
i dont know what to do to enable SHMCofig
i have a compaq 510 notebook
i also tried
[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)
but same problem goes with synclient here too
thx

edit:
when i put my 2 fingers on touhpad my pointer goes mad meaning goes rapidly into random directions.
i dont have this problem on win7 and also i have pinch zooming in win7 too

---

### Post by brettdunnam on 2010-08-26
There is actually a much easier way which is the last post of this thread: [http://ubuntuforums.org/showthread.php?t=1465996&highlight=1201n](http://ubuntuforums.org/showthread.php?t=1465996&highlight=1201n)

EDIT: I'm not sure if it works after the machine returns from sleep this way. I'll test it.

---

### Post by bigo72 on 2010-08-29
synclient-m 250  ..... and then ....

Can't access shared memory area. SHMConfig disabled? :-(

I'm googling from yesterday on how to enable it .... nothing!

I don't wont to stop here, can somebody help me?

---

### Post by brettdunnam on 2010-08-29
If you look at my post right above you, it's really simple. You don't have to do any fancy footwork, just create a script to run on startup. And yes, it still works after resuming from sleep.

Give it a shot and let me know how it goes.

---

### Post by bigo72 on 2010-12-10
OK guys, now, and now only, we can consider it SOLVED (it is usually too "rushy" to write [SOLVED] in ubuntu forums, I don't know why ...)
After a lot of time, Henrik Rydberg made the magic!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/116](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/116)

I love this man LOL

---

### Post by thelastblack on 2010-12-10
so i installed the package but "two-finger-scrolling" isnt activated yet....
i have 2finger scrolling in win7 and my touchpad is synaptics.. im using lucid now....
so that just works for eee 1201N ?

---

