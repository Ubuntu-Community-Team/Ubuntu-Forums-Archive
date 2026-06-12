---
title: "Trying to set up Pidgin Led-notification"
date: 2008-09-02
forum: General Help
---

### Post by gardara on 2008-09-02
I am trying to set up the led-notification plugin for pidgin... I want to try and make my scroll lock light or maby some other light blink when I receive a new message....

When I try to compile, all I get is this error:

```
gcc led-notification.c -O2 -Wall -fpic -g -I/usr/local/include -I/usr/local/include/gtk-2.0 -I/usr/local/include/glib-2.0 -I/usr/local/include/pango-1.0 -I/usr/local/include/atk-1.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/lib/gtk-2.0/include -I/usr/include -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include `pkg-config --cflags gtk+-2.0 pidgin` -shared -o led-notification.so
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
led-notification.c:32:20: error: notify.h: No such file or directory
led-notification.c:33:20: error: plugin.h: No such file or directory
led-notification.c:34:21: error: version.h: No such file or directory
led-notification.c:35:19: error: debug.h: No such file or directory
led-notification.c:36:18: error: cmds.h: No such file or directory
led-notification.c:37:21: error: gtkconv.h: No such file or directory
led-notification.c:38:19: error: prefs.h: No such file or directory
led-notification.c:39:22: error: gtkprefs.h: No such file or directory
led-notification.c:40:22: error: gtkutils.h: No such file or directory
led-notification.c:41:23: error: gtkplugin.h: No such file or directory
led-notification.c:42:22: error: gtkblist.h: No such file or directory
led-notification.c: In function &#8216;led_set&#8217;:
led-notification.c:45: warning: implicit declaration of function &#8216;purple_prefs_get_string&#8217;
led-notification.c:46: warning: initialisation makes pointer from integer without a cast
led-notification.c:51: warning: implicit declaration of function &#8216;purple_debug_error&#8217;
led-notification.c: In function &#8216;get_pending_list&#8217;:
led-notification.c:66: warning: initialisation makes pointer from integer without a cast
led-notification.c:68: warning: initialisation makes pointer from integer without a cast
led-notification.c:74: warning: implicit declaration of function &#8216;pidgin_conversations_find_unseen_list&#8217;
led-notification.c:74: error: &#8216;PURPLE_CONV_TYPE_IM&#8217; undeclared (first use in this function)
led-notification.c:74: error: (Each undeclared identifier is reported only once
led-notification.c:74: error: for each function it appears in.)
led-notification.c:75: error: &#8216;PIDGIN_UNSEEN_TEXT&#8217; undeclared (first use in this function)
led-notification.c:76: warning: assignment makes pointer from integer without a cast
led-notification.c:80: warning: assignment makes pointer from integer without a cast
led-notification.c:84: error: &#8216;PURPLE_CONV_TYPE_CHAT&#8217; undeclared (first use in this function)
led-notification.c:86: warning: assignment makes pointer from integer without a cast
led-notification.c:89: error: &#8216;PIDGIN_UNSEEN_NICK&#8217; undeclared (first use in this function)
led-notification.c:90: warning: assignment makes pointer from integer without a cast
led-notification.c: At top level:
led-notification.c:101: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
led-notification.c:123: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
led-notification.c:163: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
led-notification.c:171: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
led-notification.c:178: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
led-notification.c:186: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ui_info&#8217;
led-notification.c:191: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
led-notification.c:220: warning: data definition has no type or storage class
led-notification.c:220: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PURPLE_INIT_PLUGIN&#8217;
led-notification.c:220: warning: parameter names (without types) in function declaration
make: *** [led-notification.so] Error 1

```

It's like the led-notification doesn't find my pidgin...
Any ideas?

And yeah, link to the plugin: [http://simo.h.mattila.googlepages.com/led-notification](http://simo.h.mattila.googlepages.com/led-notification)

---

### Post by Mister.Vash on 2008-09-02
Do you have the pidgin dev files installed?

```

sudo apt-get install pidgin-dev

```

---

### Post by gardara on 2008-09-03
> **Mister.Vash said:**
> Do you have the pidgin dev files installed?

```

sudo apt-get install pidgin-dev

```


Didn't have that... But I just installed it and was able to compile the plugin....
However now I need to find out what controls my led's... Any Ideas? (I am using a dell xps m1210 laptop)

---

### Post by wytten on 2008-09-13
Did you have any luck?  I want this too, or something like it.

---

### Post by gardara on 2008-09-18
> **wytten said:**
> Did you have any luck?  I want this too, or something like it.

The only thing I found was how to trigger the caps luck led.. But wasn't able to get it working with pidgin :(

---

### Post by easoukenka on 2008-11-11
I am trying to install [http://www.fonomo.com/software/pidgin.html](http://www.fonomo.com/software/pidgin.html)  

However I have read I need the following dependencies but when I try to install it I get the following types of errors

gcc `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
fonomobutton.c:25:18: error: glib.h: No such file or directory
fonomobutton.c:36:20: error: notify.h: No such file or directory
fonomobutton.c:37:20: error: plugin.h: No such file or directory
fonomobutton.c:38:21: error: version.h: No such file or directory
fonomobutton.c:40:20: error: pidgin.h: No such file or directory
fonomobutton.c:42:21: error: gtkconv.h: No such file or directory
fonomobutton.c:43:23: error: gtkplugin.h: No such file or directory
fonomobutton.c:45:26: error: conversation.h: No such file or directory
fonomobutton.c:46:24: error: gtkconvwin.h: No such file or directory
fonomobutton.c:48:23: error: gtkimhtml.h: No such file or directory
fonomobutton.c:55: error: expected ‘)’ before ‘*’ token
fonomobutton.c:87: error: expected ‘)’ before ‘*’ token
fonomobutton.c:132: error: expected ‘)’ before ‘*’ token
fonomobutton.c:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
fonomobutton.c:175: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_unload’
fonomobutton.c:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
fonomobutton.c:227: error: expected ‘)’ before ‘*’ token
fonomobutton.c:231: warning: return type defaults to ‘int’
fonomobutton.c: In function ‘PURPLE_INIT_PLUGIN’:
fonomobutton.c:231: error: expected ‘{’ at end of input
make: *** [all] Error 1

When trying to install the pidgin dev I get the following error
The following packages have unmet dependencies:
  pidgin-dev: Depends: libgtk2.0-dev but it is not going to be installed

Would love to have this plugin any help would be appreciated.

---

