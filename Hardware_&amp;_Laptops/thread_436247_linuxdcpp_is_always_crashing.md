---
title: "linuxdcpp is always crashing"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Tapalunix on 2007-05-07
Hi,

I work with a Medion Laptop, AMD Athlon 2400+ and I am not a computer specialist. Nevertheless I will try to describe the problem the more detailed and comprehensible as possible.
I installed on my computer linuxdcpp.
Until two weeks ago, it worked. I got some error messages in the shell but I could still download (error message like: failure to open device).
Now, when I try to launch linuxdcpp, my computer is blocked afer a few minutes and I loose the control. I have only two solutions: waiting 15 minutes that it unblocks or shutting off (manually) my computer.
So, what did I do in between?
I think I installed a second time linuxdcpp but thanks to automatix2.
I don't know exactly how to erase completely a program with Linux. Just to erase the files is not enough since I made it and the program could still have been launched.
I also tried to install a webcam inbetween and I installed a driver from automatix2 (spca5xx-20060501)

Here the error messages that I get:
(linuxdcpp:5099): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:5099): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:5099): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:5099): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
Bus error

I am pretty sure that someone will tell me: It sounds not good!

I have other problems but one after one!

Thanks!

---

### Post by Rhadamanthos on 2007-05-09
I've seen those error messages when shutting down linuxdcpp before, but not during. I STRONGLY suggest that you go out and follow the instructions for building this package from source!

Linuxdcpp is under heavy development - they've fixed a lot of resource-use and crash bugs recently, and automatix probably doesn't have the most recent build from the project.

Follow the instructions here: [http://ubuntuforums.org/showthread.php?t=193984](http://ubuntuforums.org/showthread.php?t=193984)

That should get you going! :)

---

### Post by Tapalunix on 2007-05-10
Hey, hi!

I was desesperating that nobody answered to me.
Actually I already done exactly what you advised to me, this howto is really good made but the same problem appeared.
When I use automatix some similar error messages appears as well:

laurent@laurent-laptop:~/Photos$ automatix2
true
Starting
/usr/lib/automatix2/resin_ui.py:60: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
  self.show_apps.set_menu(self.view_menu);
TRAY ICON CREATED

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/lib/automatix2/main_interface.py", line 166, in switch_type_page

tree.set_cursor(self.saved_cat[self.type_state] )
TypeError
:
could not convert path to a GtkTreePath


(automatix.py:10043): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed



I made something wrong but I don't know what; where and when!

Help, Help!!

---

### Post by Rhadamanthos on 2007-05-11
Boy, that's a funky problem. It sounds like some dependency is messed up, but I'll be the first to admit that I'm in over my head here.

One thing I do know is that the first Automatix had problems with forcing people to use outdated or wrong packages using --force-yes (in otherwords, even if the prompt is "warning, doing this will seriously muck up your system" it would still say yes)

I don't know if the current automatix has any problems like these, but the first thing I would check is start synaptic ( "sudo synaptic" or  ) and go edit-> fix broken packages.

See if anything comes up. Also check under "Status" (big button on the front panel) and see if there's anything in an odd status. 

Sorry I can't be of more help, but it sounds like a tricky bug. It's probably in automatix or something automatix did for you, though.

---

### Post by Tapalunix on 2007-05-13
I don't have synaptic!

Can you explain me what for do I need synaptic?

Thanks

---

### Post by Rhadamanthos on 2007-05-14
... What version of Ubuntu are you using?

Synaptic comes by default with every version I've ever used. It's a graphical front-end for your package manager (apt). It's a lot easier than doing things by hand, or with some of the older utilities like dpkg or aptitude.


Try opening up a terminal and typing "synaptic" if you didn't try that. I'm not sure if/where it appears in the menus.

---

### Post by Tapalunix on 2007-05-14
I am using Kubuntu and more precisely:
laurent@laurent-laptop:/$ cat /proc/version
Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Mar 13 23:32:38 UTC 2007 (Ubuntu 2.6.17-11.37-generic)

and here you can see what I tried to do:

laurent@laurent-laptop:~$ synaptic
bash: synaptic: command not found

So I will install synaptic and then I will post you the next message.

---

### Post by Tapalunix on 2007-05-14
Here we go, after installing synaptic, I launched it and I received:

root@laurent-laptop:/# synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:6383): Gtk-WARNING **: cannot open display:
root@laurent-laptop:/# sudo -i -u laurent
laurent@laurent-laptop:~$ synaptic


(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:6400): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

Although there is some error messages, it seems that Synaptic is working because I installed GYachE. I don't know if GYachE is working because I don't know my server, anyway it has been installed and it seems to work. 
I installed as well valknut and I have to test it.
I will know tried to launch again linuxdcpp.

To be continued...

---

### Post by Rhadamanthos on 2007-05-14
Yup, I'm out of my league here. Sorry, but I don't think I'll be able to help you more. It may be related to you using kubuntu rather than Ubuntu - some of my friends have had problems with things that should be defaults on Ubuntu not being on Kubuntu - even when they're not Gnome-based programs.

I dunno where you should go from here, but maybe someone else will come along and help you out. Are there Kubuntu forums you could check, or is this it?

Anyhow, best of luck. If you have any more questions I'll try and help best I can, but I'm too much of a newb to get you running on this one.

---

