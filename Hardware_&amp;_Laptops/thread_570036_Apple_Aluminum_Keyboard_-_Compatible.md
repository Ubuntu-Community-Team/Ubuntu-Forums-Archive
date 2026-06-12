---
title: "Apple Aluminum Keyboard - Compatible?"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by Perfex on 2007-10-07
Im curious if the new apple aluminum keyboard, either wired or wireless is compatible with ubuntu?

Just wondering if anyone has used it on ubuntu and if there are drivers for it 
[http://www.apple.com/keyboard/](http://www.apple.com/keyboard/)

[http://docs.info.apple.com/article.html?artnum=304270](http://docs.info.apple.com/article.html?artnum=304270) Here it says it works with xp via bootcamp drivers

---

### Post by roastbeef on 2007-10-10
I just bought one today - wired version.  Works great so far, all the keys that are supposed to work seem to.  The Num Lock button has been replaced with 'clear' although on my machine it still behaves like 'Num Lock' (so when you use the keypad and nothing is happening, press 'clear').

The 'eject' button also works to eject the drive but not to close it (apparently this is a bug: [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/37785](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/37785))

What I don't know yet is if I could ever get F13-F19 working.  They don't seem to do anything right now (which I expected), but it would be nice to tie those keys to some hot-keys and compiz-related things.

---

### Post by Perfex on 2007-10-10
thankyou for the response :)

---

### Post by roastbeef on 2007-10-10
No problem. :)

It seems compiz had no trouble recognizing F13-F16, but didn't pick up F17-F19.  xev was able to discover all of the keys however.

If I figure something out I will post to let you know.

---

### Post by jkakar on 2007-10-11
I have the wireless version.  It feels great and mostly works.  I
added /etc/modprobe.d/applekeyboard with the following contents:

options hid pb_fnmode=2

To make the function keys work as function keys.  The Fn key does not
work which means no multimedia keys or home/end, pgup/pgdn, nor
delete.  So far the lack of these keys hasn't been a particularly big
deal for me.  I might try the thing mentioned here at some point:

[http://ulkoavaruus.de/index.php?doc=ibm_keyboard](http://ulkoavaruus.de/index.php?doc=ibm_keyboard)

or perhaps see if pommed can be made to enable the Fn key.  One nit I
have, and I don't know if it's bluetooth-related, specific to this
keyboard or related to something else, is that hitting CapsLock (which
I remap to Ctrl) and a letter quickly often just registers the letter.
I don't know if this behaviour is the same when using the real Ctrl
key, since I pretty much never use it.  So, I'm finding myself having
to C-a and other such keys a little slower than my normal typing
speed.

---

### Post by Perfex on 2007-10-12
Interesting the wireless one I would of thought wouldnt of worked, I am used to my[ Deck keyboard]("http://deckkeyboards.com") being small (without number pad) so the wireless may be more my style.

Thanks both of you for the replys, I am more interested in using them for the systems I sell then anything, although I still have to get one for my self ;)

---

### Post by jkakar on 2007-11-20
Gah.  Figured out why CapsLock doesn't respond as I expect:

[http://rentzsch.com/notes/applesantiCAPSLOCK](http://rentzsch.com/notes/applesantiCAPSLOCK)

---

### Post by buddhaguy on 2008-01-08
The wireless works a dream apart from the extra keys need mapping somehow but I am yet to figure out how to get it to connect smoothly after it goes in to power saving.

At login its possible to just start typing but if the keyboard goes in to power saving it still shows as connected in the bluetooth panel but the keyboard needs to be switched off and back on again, about a 15 second delay!

Once thats sorted it'll be perfect :)

Later
G

---

### Post by ScottKinkade on 2008-03-04
I have the new apple bluetooth keyboard (aluminum) and i am typing on it right now, so it's connected, but apparently the keyboard has an automatic sleep feature meaning it goes to sleep and thus, disconnects with my computer and therefore i have to go to teminal and type: sudo hidd --connect 00:1E:52:F8:63:40 every time i come back to my computer. This is quite an issue since i have to TYPE that in to connect the device i need to type it with... Is there some way to make it automatically connect? Or is there some way to make a little executable file that does that command for me??? I have Gutsy and I need some help...

---

### Post by jkakar on 2008-03-04
Hi,

Have you tried following the instructions in the "Connect Devices at Startup" section of [https://help.ubuntu.com/community/BluetoothSetup?](https://help.ubuntu.com/community/BluetoothSetup?)  That's what I did and the sleep/lose connection issue went away.

Hope this helps,
J.

---

### Post by ScottKinkade on 2008-03-04
Thank you! I just did that and now we wait till the keyboard goes to sleep to see if it connects automatically! Thank you!!!

---

### Post by ScottKinkade on 2008-03-04
Hey, i tried that and it didn't work :-( is there any kind of thing i could just double click on or something that would run the sudo hidd --connect 00:1E:52:F8:63:40 command for me??? or something like that??? Or is there like something else i should try?

---

### Post by buddhaguy on 2008-03-05
What works for me is to switch the keyboard off and on again and it reconnects. So surely theres a method between the two that would reconnect automatically. Still trying :)

---

### Post by ScottKinkade on 2008-03-06
IT WORKED!!! I just have to turn it off and on again every time and it works. Thank you so much!!!

---

### Post by jkakar on 2008-03-06
Ah, nice, glad to hear it. :)  I found that I could just press a key and wait a few seconds and then it would wake up.  But that's about the same as power cycling it.

---

### Post by alessandro.crugnola on 2008-04-10
I have a similar problem..
I have an apple aluminium usb, and it worked since 2 days ago when I updated the latest 2.6.24-15 kernel..
now it doesn't work at all.. it's strange because it works in the login screen, but once gnome has loaded it stops work completely. every key seems to be mapped incorrectly ( eg.' U' print '5' )

I have to wait for a new kernel update? or is there something I can do?

alessandro

---

### Post by FullPrime on 2008-04-10
Has anyone got the FN key working with the wireless keyboard?  

I have the keyboard hooked up and it feels really good.  But I'm a coder and I do a lot of editing.  I really need HOME/END/PageUp/PageDn.  Older editors like VI and emacs have multi-key mappings but the newer visual IDEs expect the extended editing keys

On my system the function keys (Fx) worked right away.  And I was surprised when the eject key work.

Finally I checked out the site [http://ulkoavaruus.de/](http://ulkoavaruus.de/) recommended earlier in this thread but I only get empty pages.

/FullPrime

---

### Post by plasmatonic on 2008-04-16
> **alessandro.crugnola said:**
> I have a similar problem..
I have an apple aluminium usb, and it worked since 2 days ago when I updated the latest 2.6.24-15 kernel..
now it doesn't work at all.. it's strange because it works in the login screen, but once gnome has loaded it stops work completely. every key seems to be mapped incorrectly ( eg.' U' print '5' )

I have to wait for a new kernel update? or is there something I can do?

alessandro

Try hitting F6 (without the usage of fn). By default Ubuntu maps the keyboard strangely. The clear button will enable Numlock, but on the letter keys as if the keyboard was a laptop. When I have the time to find the right settings for the keyboard, I'll post back.

---

### Post by plasmatonic on 2008-04-16
After digging around on launchpad.net this is a pretty well documented issue. Like I guessed, the clear key sends the numlock functionality like it should, but then the kernel is seeing the keyboard as a powerbook keyboard and causing the numlock to remap letter keys as if it were small form. 

The simplest solution (as per a comment on the bug submission):
A workaround I found was to enable the keypad numbers by default by going to System > Preferences > Keyboard > (Layouts Tab) > Layout Options... > Miscellaneous Compatibility Options, and checking "Default numeric keys" and "Numeric keypad keys work as with Mac."

However, if you hit the clear button, you will encounter the issue still, but at least your numpad works.

Additionally, there are working patches that require you recompile the kernel to fix the issue. As of now, this is not in the Hardy commits, but it is being pushed for and *might* make it before the release date, else soon after.

---

### Post by alessandro.crugnola on 2008-04-21
Thank you very much! This solved my problem :)

---

### Post by ZAxisMapping on 2008-06-17
Thanks plasmatonic, your advice was quite helpful.  Does anyone know of any updates to get full functionality from this keyboard?

Also, is there a way to remap the "command key" to "alt"?  (I pick up bad habits at work while running Windows).

---

