---
title: "Cairo Dock Crashes Constantly"
date: 2008-10-20
forum: General Help
---

### Post by kpmoore on 2008-10-20
I've played around with it for a while and I can't seem to figure out why it keeps crashing. The little callback space disappears whenever I click on any of the icons/menus in the upper taskbar. Only way to get it back is go through the Applications menu.

Any ideas?

---

### Post by kpmoore on 2008-10-20
bump

---

### Post by loomsen on 2008-10-21
Run cairo by typing cairo-dock into a terminal, and see what it spits out when cairo crashes.

---

### Post by fabounet on 2008-10-22
which version ?
latest in 1.6.2, and 1.6.3 is for the end of the month.

---

### Post by bixejo on 2009-01-17
Hi, kpmoore.

Did you get a solution for this? I'm getting the same problem right now.

Thank you,

---

### Post by Wage Slave on 2009-01-18
I have this problem as well. It seems to crash everytime I maximise or minimise a window. Does anyone have a fix for this?

---

### Post by bixejo on 2009-01-18
I've realized that the dock is still up and running, but for some reason the callback area is missing.

If you associate a keyboard shortcut in the cairo-doc configuration window to hide/show the dock, it reappears again as soon as you press that key in the very screen place where the mouse pointer is at.

It's not a solution (for me at least) but it reveals that the dock actually doesn't crash, but just its callback area disappears for some reason, which sounds like a dock misbehaviour.

---

### Post by castoroil97 on 2009-01-18
I believe I am having this error 
seems like it runs, but does not come up...


Run in terminal:

:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_get_desklet_decoration (personnal)
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed
warning :  (cairo-dock-load.c:cairo_dock_load_task_indicator:787)  
  couldn't load image '/home/pico/.cairo-dock/Indicateur cairo dock/1208712452.svg' for indicators
nouvelle icone d'appli (52429142)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
 insertion de Ubuntu Forums - Reply to Topic - Mozilla Firefox apres Maintenance -> iSeparatorType : 1
nouvelle icone d'appli (56623358)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
nouvelle icone d'appli (20972311)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
nouvelle icone d'appli (16777219)
nouvelle icone d'appli (16777254)
nouvelle icone d'appli (44040202)
iRotation:0°
decorations : default
 insertion de Weather apres gedit -> iSeparatorType : 3
iRotation:0°
decorations : default
iRotation:0°
decorations : default
iRotation:0°
decorations : default
iRotation:0°
decorations : default
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Failed to open file '/home/castoroil69/.cairo-dock/current_theme/launchers/dustbin-empty.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Failed to open file '/home/castoroil69/.cairo-dock/current_theme/launchers/dustbin-full.png': No such file or directory
warning :  (applet-init.c:_load_theme:72)  
  Attention : couldn't find images, this theme is not valid
  MaJ des decorations du fond -> 990.00x40.00
add personnal
add default
add personnal
weather : applet : 93af7c8, icon : 9326880, subdock <- 916bb60
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 44040202 => {0 ; 0 ; 1 ; 0}
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 56623358 => {0 ; 0 ; 1 ; 0}
new backing pixmap (bis) : 41943047
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 52429142 => {0 ; 0 ; 1 ; 0}
new backing pixmap (bis) : 41943049

---

### Post by castoroil97 on 2009-01-18
I can see that it is working in the terminal, but nothing happens on the desktop

---

### Post by fabounet on 2009-01-19
try to deactivate the taskbar option that says to hide the dock on maximize windows.
also try to set up the size of the callback area, maybe it's tiny.

---

### Post by srpayo on 2009-03-06
I also have the same problem with latest version of cairo-dock. 

The call-back icon disappears randomly when opening applications and the easiest way to get it back is to use the hotkeys specified in the properties. 

I think this must be a general bug as it seems to be happening to some other people from what I can see. Anyone found a solution yet?

Else lets report it to the cairo-dock developers...right?

cheers

---

### Post by bixejo on 2009-04-03
I realized that cairo-dock works fine in my desktop box but shows all problems described in this thread in my laptop.

In my desktop box I've installed a 32bit edition, but in my laptop it's a 64bit edition. In the 32bit repos the last available version is 1.6.3, but in the 64bit it's 1.6.0.

Maybe this' something to do with the problem you all are getting too?

---

### Post by Stray Wolf on 2011-06-13
I love this place.  Such knowledgeable people to hopefully learn from.  I've been having problems with cairo-dock for the first time ever as well.  It remembers all but one setting upon restart.  It always starts with a second bottom dock I have to delete on every start up.  If anything could be solved here I'd like to fix why it crashes when I try to access rhythmbox from the desktop applet I have set as the CD_box.  Here's the terminal stuff:

laptop:~$ cairo-dock -o
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================ 
    Cairo-Dock version: 2.3.0~2
    Compiled date:  May 29 2011 11:40:02
    Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:699)  
  while listing user packages in '/home/justin/.config/cairo-dock/third-party' : Error opening directory '/home/justin/.config/cairo-dock/third-party': No such file or directory
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.

(rhythmbox:3281): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `filename != NULL' failed

(rhythmbox:3281): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/umusicstore/__init__.py", line 58, in activate
    icon = gtk.gdk.pixbuf_new_from_file_at_size(icon_file_name, 22, 22)
TypeError: pixbuf_new_from_file_at_size() argument 1 must be string, not None
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:272)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now (cairo-dock -o).
Feel free to report this bug on glx-dock.org to help improving the dock !
info on the system :
** (rhythmbox:3281): DEBUG: Loading the real store page
Linux Zero-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
Couldn't guess if it was an applet's fault or not. It may have crashed inside the core or inside a thread

** (rhythmbox:3281): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DYTVsYjewlemftxBO13z_mCe%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1307994403%26oauth_token%3DdqSMRVP47pVRsQdZZNvg%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&5Rbkx1Px3RTPlm6g1Rcc100J31kwqXF044sC5qGK62hkTk7BwXjxJQnDJ7Xbwgbdz09V2d6GdCDk7rX3'

** (rhythmbox:3281): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=YTVsYjewlemftxBO13z_mCe&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1307994403&oauth_token=dqSMRVP47pVRsQdZZNvg&oauth_verifier=None&oauth_version=1.0&oauth_signature=4Ypy2jd4GL4DpPJ799YYcUwGR8c%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=YTVsYjewlemftxBO13z_mCe&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1307994403&oauth_token=dqSMRVP47pVRsQdZZNvg&oauth_verifier=None&oauth_version=1.0&oauth_signature=4Ypy2jd4GL4DpPJ799YYcUwGR8c%3D)
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================ 
    Cairo-Dock version: 2.3.0~2
    Compiled date:  May 29 2011 11:40:02
    Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:699)  
  while listing user packages in '/home/justin/.config/cairo-dock/third-party' : Error opening directory '/home/justin/.config/cairo-dock/third-party': No such file or directory
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:272)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now (cairo-dock -o -m).
Feel free to report this bug on glx-dock.org to help improving the dock !
info on the system :
Linux-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
Couldn't guess if it was an applet's fault or not. It may have crashed inside the core or inside a thread
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================ 
    Cairo-Dock version: 2.3.0~2
    Compiled date:  May 29 2011 11:40:02
    Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
g_key_file_set_string: assertion `string != NULL' failed
g_key_file_set_string: assertion `string != NULL' failed
g_key_file_set_string: assertion `string != NULL' failed
g_key_file_set_string: assertion `string != NULL' failed
** (rhythmbox:3281): DEBUG: navigation requested to [http://stores.7digital.com/user/partnerLogin.aspx?shop=480&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D480%26partner%3D983&oauth_nonce=85151320&oauth_timestamp=1307994405&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=246735&oauth_version=1.0&oauth_signature=mlljqmu3Em4tz93PCs5Uyo3nxS8%3D&partner=983](http://stores.7digital.com/user/partnerLogin.aspx?shop=480&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D480%26partner%3D983&oauth_nonce=85151320&oauth_timestamp=1307994405&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=246735&oauth_version=1.0&oauth_signature=mlljqmu3Em4tz93PCs5Uyo3nxS8%3D&partner=983)
cairo_dock_set_status_message ()
cairo_dock_set_status_message (Listing themes in 'themes2.2' ...)
cairo_dock_set_status_message ()
showing the maintenance mode ...
** (rhythmbox:3281): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=480&partner=983](http://stores.7digital.com/default.aspx?shop=480&partner=983)
cairo_dock_set_status_message ()
end of the maintenance mode.
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:699)  
  while listing user packages in '/home/justin/.config/cairo-dock/third-party' : Error opening directory '/home/justin/.config/cairo-dock/third-party': No such file or directory
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
warning :  (/build/buildd/cairo-dock-2.3.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:272)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now (cairo-dock -o -m -m).
Feel free to report this bug on glx-dock.org to help improving the dock !
info on the system :
Linux laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
Couldn't guess if it was an applet's fault or not. It may have crashed inside the core or inside a thread
Sorry, Cairo-Dock has encoutered some problems, and will quit.
laptop:~$ Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/umusicstore/__init__.py", line 86, in deactivate
    self.source.delete_thyself()
AttributeError: 'U1MusicStorePlugin' object has no attribute 'source'

---

### Post by Stray Wolf on 2011-06-22
I submitted a report to cairo-dock on Launchpad.  I got a response within 45 minutes of reporting my bug.  He had me install a debug tool and the bazaar version of cairo.  Last Wednesday (6/15/11) I submitted the screenshot from the debug tool as per instructions from the responder on Launchpad.  As of Monday (6/19/11) the fix was already in an update.  Beat that Microshaft!

---

