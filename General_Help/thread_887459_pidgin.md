---
title: "pidgin"
date: 2008-08-12
forum: General Help
---

### Post by 0perator on 2008-08-12
when i start pidgin it loads for like 2 seconds then just closes

i dont know what could have caused it but here is the output when i try and open it from terminal

```

thomas@linux:~$ pidgin
*** glibc detected *** pidgin: double free or corruption (fasttop): 0x08589ba8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74b4a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb74b84f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7747c61]
/usr/lib/libpurple.so.0(purple_proxy_get_setup+0x26f)[0xb7863a3f]
/usr/lib/libpurple.so.0(purple_proxy_connect+0x87)[0xb7863e27]
/usr/lib/libpurple.so.0[0xb7876fbf]
/usr/lib/libpurple.so.0[0xb787d944]
pidgin[0x80a47c3]
/usr/lib/libglib-2.0.so.0[0xb77740ed]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb773fdd6]
/usr/lib/libglib-2.0.so.0[0xb7743193]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb7743577]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7d3e264]
pidgin(main+0x76f)[0x80bc39f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb745f450]
pidgin[0x806b031]
======= Memory map: ========
08048000-08101000 r-xp 00000000 08:03 584555     /usr/bin/pidgin
08101000-08104000 rw-p 000b8000 08:03 584555     /usr/bin/pidgin
08104000-085a2000 rw-p 08104000 00:00 0          [heap]
ad000000-ad021000 rw-p ad000000 00:00 0 
ad021000-ad100000 ---p ad021000 00:00 0 
ad162000-ad1c2000 rw-s 00000000 00:09 24412219   /SYSV00000000 (deleted)
ad1c2000-ad222000 rw-s 00000000 00:09 24313903   /SYSV00000000 (deleted)
ad222000-ad225000 r-xp 00000000 08:03 147881     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
ad225000-ad226000 rw-p 00002000 08:03 147881     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
ad226000-ad32a000 rw-p ad226000 00:00 0 
ad32a000-ad3b1000 r--p 00000000 08:03 255458     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
ad3b1000-ad4b5000 rw-p ad3b1000 00:00 0 
ad4b5000-ad4b7000 r-xp 00000000 08:03 475255     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
ad4b7000-ad4b8000 rw-p 00001000 08:03 475255     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
ad4b8000-ad549000 r--p 00000000 08:03 255459     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ad549000-ad54f000 r--s 00000000 08:03 337127     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
ad54f000-ad552000 r--s 00000000 08:03 338218     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
ad552000-ad553000 r--s 00000000 08:03 338216     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
ad553000-ad554000 r--s 00000000 08:03 338188     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
ad554000-ad557000 r--s 00000000 08:03 338186     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
ad557000-ad55e000 r--s 00000000 08:03 337116     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
ad55e000-ad561000 r--s 00000000 08:03 338103     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
ad561000-ad569000 r--s 00000000 08:03 338102     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
ad569000-ad571000 r--s 00000000 08:03 338101     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
ad571000-ad572000 r--s 00000000 08:03 338100     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
ad572000-ad594000 r--s 00000000 08:03 337907     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
ad594000-ad597000 r--s 00000000 08:03 338099     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
ad597000-ad59e000 r--s 00000000 08:03 338098     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
ad59e000-b6da5000 r--p 00000000 08:03 2772777    /home/thomas/.icons/OxygenRefit2-orange-version/icon-theme.cache
b6da5000-b6dcd000 r-xp 00000000 08:03 762346     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6dcd000-b6dce000 rw-p 00028000 08:03 762346     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6dce000-b6e06000 r-xp 00000000 08:03 2138188    /usr/lib/purple-2/libyahoo.so
b6e06000-b6e08000 rw-p 00037000 08:03 2138188    /usr/lib/purple-2/libyahoo.so
b6e08000-b6e0b000 r-xp 00000000 08:03 1851460    /lib/libgpg-error.so.0.3.0
b6e0b000-b6e0c000 rw-p 00002000 08:03 1851460    /lib/libgpg-error.so.0.3.0
b6e0c000-b6e1b000 r-xp 00000000 08:03 116798     /usr/lib/libtasn1.so.3.0.12
b6e1b000-b6e1c000 rw-p 0000e000 08:03 116798     /usr/lib/libtasn1.so.3.0.12
b6e1c000-b6e67000 r-xp 00000000 08:03 1851458    /lib/libgcrypt.so.11.2.3
b6e67000-b6e69000 rw-p 0004a000 08:03 1851458    /lib/libgcrypt.so.11.2.3
b6e69000-b6eda000 r-xp 00000000 08:03 115334     /usr/lib/libgnutls.so.13.9.1
b6eda000-b6edf000 rw-p 00071000 08:03 115334     /usr/lib/libgnutls.so.13.9.1
b6ee0000-b6ee6000 r--s 00000000 08:03 337114     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6ee6000-b6ee8000 r--s 00000000 08:03 337104     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6ee8000-b6eec000 r-xp 00000000 08:03 149072     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6eec000-b6eed000 rw-p 00003000 08:03 149072     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6eed000-b6eef000 r-xp 00000000 08:03 2138191    /usr/lib/purple-2/idle.so
b6eef000-b6ef0000 rw-p 00001000 08:03 2138191    /usr/lib/purple-2/idle.so
b6ef0000-b6ef2000 r-xp 00000000 08:03 2138209    /usr/lib/purple-2/psychic.so
b6ef2000-b6ef3000 rw-p 00001000 08:03 2138209    /usr/lib/purple-2/psychic.so
b6ef3000-b6ef7000 r-xp 00000000 08:03 2138178    /usr/lib/purple-2/ssl-gnutls.so
b6ef7000-b6ef8000 rw-p 00003000 08:03 2138178    /usr/lib/purple-2/ssl-gnutls.so
b6ef8000-b6f0c000 r-xp 00000000 08:03 2138164    /usr/lib/purple-2/libzephyr.so
b6f0c000-b6f0d000 rw-p 00013000 08:03 2138164    /usr/lib/purple-2/libzephyr.so
b6f0d000-b6f10000 rw-p b6f0d000 00:00 0 
b6f10000-b6f1a000 r-xp 00000000 08:03 2138207    /usr/lib/purple-2/libsimple.so
b6f1a000-b6f1b000 rw-p 00009000 08:03 2138207    /usr/lib/purple-2/libsimple.so
b6f1b000-b6f2b000 rw-p b6f1b000 00:00 0 
b6f2b000-b6f2d000 r-xp 00000000 08:03 2138163    /usr/lib/purple-2/joinpart.so
b6f2d000-b6f2e000 rw-p 00001000 08:03 2138163    /usr/lib/purple-2/joinpart.so
b6f2e000-b6f2f000 r-xp 00000000 08:03 2138198    /usr/lib/purple-2/ssl.so
b6f2f000-b6f30000 rw-p 00000000 08:03 2138198    /usr/lib/purple-2/ssl.so
b6f30000-b6f32000 r-xp 00000000 08:03 2138208    /usr/lib/purple-2/offlinemsg.so
b6f32000-b6f33000 rw-p 00001000 08:03 2138208    /usr/lib/purple-2/offlinemsg.so
b6f33000-b6f51000 r-xp 00000000 08:03 2138199    /usr/lib/purple-2/libgg.so
b6f51000-b6f52000 rw-p 0001e000 08:03 2138199    /usr/lib/purple-2/libgg.so
b6f52000-b6f53000 r-xp 00000000 08:03 2138200    /usr/lib/purple-2/buddynote.so
b6f53000-b6f54000 rw-p 00000000 08:03 2138200    /usr/lib/purple-2/buddynote.so
b6f54000-b6f6d000 r-xp 00000000 08:03 2138206    /usr/lib/purple-2/libnovell.so
b6f6d000-b6f6e000 rw-p 00018000 08:03 2138206    /usr/lib/purple-2/libnovell.so
b6f6e000-b6fa1000 r-xp 00000000 08:03 2138162    /usr/lib/purple-2/libjabber.so.0.0.0
b6fa1000-b6fa3000 rw-p 00032000 08:03 2138162    /usr/lib/purple-2/libjabber.so.0.0.0
b6fa3000-b6fa5000 rw-p b6fa3000 00:00 0 
b6fa5000-b6fa7000 r-xp 00000000 08:03 2138183    /usr/lib/purple-2/libxmpp.so
b6fa7000-b6fa8000 rw-p 00002000 08:03 2138183    /usr/lib/purple-2/libxmpp.so
b6fa8000-b6faa000 r-xp 00000000 08:03 2138202    /usr/lib/purple-2/statenotify.so
b6faa000-b6fab000 rw-p 00001000 08:03 2138202    /usr/lib/purple-2/statenotify.so
b6fab000-b6fad000 r-xp 00000000 08:03 2138179    /usr/lib/purple-2/autoaccept.so
b6fad000-b6fae000 rw-p 00001000 08:03 2138179    /usr/lib/purple-2/autoaccept.so
b6fae000-b6fb6000 r-xp 00000000 08:03 2138161    /usr/lib/purple-2/log_reader.so
b6fb6000-b6fb7000 rw-p 00008000 08:03 2138161    /usr/lib/purple-2/log_reader.so
b6fb7000-b6fe1000 r-xp 00000000 08:03 2138201    /usr/lib/purple-2/libqq.so
b6fe1000-b6fe2000 rw-p 0002a000 08:03 2138201    /usr/lib/purple-2/libqq.so
b6fe2000-b6fe3000 r-xp 00000000 08:03 2138169    /usr/lib/purple-2/newline.so
b6fe3000-b6fe4000 rw-p 00000000 08:03 2138169    /usr/lib/purple-2/newline.so
b6fe4000-b6fe5000 r-xp 00000000 08:03 2138197    /usr/lib/purple-2/ssl-nss.so
b6fe5000-b6fe6000 rw-p 00000000 08:03 2138197    /usr/lib/purple-2/ssl-nss.so
b6fe6000-b700f000 r-xp 00000000 08:03 2138182    /usr/lib/purple-2/libmsn.so
b700f000-b7010000 rw-p 00029000 08:03 2138182    /usr/lib/purple-2/libmsn.so
b7010000-b7013000 rw-p b7010000 00:00 0 
b7013000-b7014000 r-xp 00000000 08:03 2138194    /usr/lib/purple-2/libicq.so
b7014000-b7015000 rw-p 00001000 08:03 2138194    /usr/lib/purple-2/libicq.so
b7015000-b7053000 r-xp 00000000 08:03 2138210    /usr/lib/purple-2/liboscar.so.0.0.0
b7053000-b7055000 rw-p 0003d000 08:03 2138210    /usr/lib/purple-2/liboscar.so.0.0.0
b7055000-b7056000 r-xp 00000000 08:03 2138190    /usr/lib/purple-2/libaim.so
b7056000-b7057000 rw-p 00001000 08:03 2138190    /usr/lib/purple-2/libaim.so
b7057000-b7069000 r-xp 00000000 08:03 2138170    /usr/lib/purple-2/libirc.so
b7069000-b706a000 rw-p 00011000 08:03 2138170    /usr/lib/purple-2/libirc.so
b706a000-b707f000 r-xp 00000000 08:03 2138165    /uAborted

```

thanks.

---

### Post by 0perator on 2008-08-12
bump...

anyone?

---

### Post by svlad cjelli on 2008-08-12
did you try to reinstall pidgin?

something like that:

```
sudo apt-get remove pidgin
sudo apt-get autoremove
sudo apt-get install pidgin
sudo apt-get update
```

bombolo bituna
Svlad

---

### Post by 0perator on 2008-08-12
yeah ive tried that with 

```

apt-get purge pidgin

```

and reinstalled

still the same

---

### Post by eldragon on 2008-08-12
disable sounds.......... see if it works.... this happens to me from time to time, i think its either pidgin or pulseaudio...

search launchpad for that problem.... its bound to be somewhere..

---

### Post by Aeph on 2008-08-12
> **eldragon said:**
> disable sounds.......... see if it works.... this happens to me from time to time, i think its either pidgin or pulseaudio...

Yeah, either try that or open Pidgin before opening anything else when you boot up your machine. If it still doesn't work, then it probably isn't the audio.

---

### Post by 0perator on 2008-08-12
how do i disable them if i cant even open it

and i think they are already disabled cos they annoyed me

EDIT:

just rebooted and still no luck, what to look for on launchpad i have never used it before?

---

### Post by ragflan on 2008-08-12
First, create a new user account and see if Pidgin is running fine on that user account. If yes, then:

Try this. There should be some of your settings that's screwing things around, maybe? I'm not sure. You can try this:

1.) There's a **hidden folder** titled **.purple** in your Home folder. That should be your settings for Pidgin linked to your user account on Ubuntu. Just like how .mozilla has all your extensions and bookmarks and stuff for Firefox.
2.) Copy that folder and place it elsewhere for the meantime. (Like on the Desktop or just somewhere other than Home folder).
3.) Then delete the folder **.purple** in your Home folder. 
4.) Uninstall Pidgin and then reinstall it. **(This step I think you can skip, but do it anyway.)**
5.) Run Pidgin.

It should create a new directory .purple again in your Home folder and hopefully it should run fine. But remember that your settings for your Pidgin (like added plugins or chat logs) from before won't be there as your settings folder is a new one now.

If it doesn't solve anything, remember the folder you copied out of your Home drive? The **.purple** folder? Put in back in your Home drive.

---

### Post by 0perator on 2008-08-12
i moved it

and now it comes up with the add account dialogue

and then after 2 seconds it dissapears again 

:(

---

### Post by 0perator on 2008-08-12
bump

anyone?

---

### Post by syko21 on 2008-08-12
[www.getdeb.net](www.getdeb.net) has updated versions of pidgin compared to the repositories. You should try to install the latest version.

---

### Post by ragflan on 2008-08-12
This is not much of a solution, but you can install and try **Emesene** in the meantime. It's in the repositories. Or get the SVN version from [http://www.emesene.org/](http://www.emesene.org/) (Why I suggested this is because, the version found in the repositories sometimes doesn't load the contact list, but the SVN version always does.)

I used to use Pidgin for the way it looks and all the functionality. Emesene looks better than Pidgin (at least to me) and the functionality is somewhat there as well. 

If you use Google Talk instead of MSN, then I suggest in the meantime to use Google Talk through Prism while waiting on a solution.

Also, did you try using Pidgin in a new user account? 

1.) Go to System --> Administration --> Users and Groups.
2.) Unlock it with your password.
3.) Add User - set username and password.
4.) Login with the new user and try Pidgin.

If it works, then it's something just related to your account.

---

