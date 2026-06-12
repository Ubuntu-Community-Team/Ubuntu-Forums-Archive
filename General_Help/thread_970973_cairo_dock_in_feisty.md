---
title: "cairo dock in feisty"
date: 2008-11-04
forum: General Help
---

### Post by thomasboleyn on 2008-11-04
Hi there, I'm trying to get cairo dock to work in feisty at the moment. I've satisfied all the dependencies mentioned on this page ([https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)) under the 'deb' section, and then I downloaded and installed the latest dock and plugin debs from [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724) .
I opened the dock from 'Applications / system tools', and a manager box popped up that asked me for a theme, so I picked a mac-eqsuqe one, but after this there wasn't a dock in sight. Now when I click the same icon, nothing happens. When I try running 'cairo-dock' in the terminal, it shows the cairo dock icon on my awn dock, but it then closes instantly. When I runi 'cairo-dock -m' in the terminal, it brings up the cairo dock manager box that lets me customize it in a million different ways, but at no point can I ever see,  the dock, and when I close the manager it still doesn't appear. 

As I am using feisty I have had to get compiz up and running through a backport, and everything has always run flawlessly with it (awn etc). This is the only thing I can think of that may be stopping it appearing.

Any help would be appreciated! Thanks.:KS

---

### Post by fabounet on 2008-11-05
what gives "cairo-dock -l debug" in a terminal ?
isn't it hidden somewhere ?

---

### Post by thomasboleyn on 2008-11-05
It's definitely not hidden anywhere, as there is no mention of it in the system log/monitor, and no screen edges make it pop up. I'll paste what "cairo-dock -l debug" coughs up when I get home from work.:confused:

---

### Post by thomasboleyn on 2008-11-05
> **fabounet said:**
> what gives "cairo-dock -l debug" in a terminal ?
isn't it hidden somewhere ?

Ok, this is what it gives me:

```
thomas@thomas-laptop:~$ cairo-dock -l debug
message :  (cairo-dock.c:main:435)  
  Compiled with Glitz (hardware acceleration support)n
message :  (cairo-dock-dock-manager.c:cairo_dock_initialize_dock_manager:59)  
  
message :  (cairo-dock-renderer-manager.c:cairo_dock_initialize_renderer_manager:172)  
  
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (default)
debug   :  (cairo-dock-X-utilities.c:cairo_dock_get_nb_viewports:373)  
  pVirtualScreenSizeBuffer : 5120x800
message :  (cairo-dock.c:main:587)  
  environnement de bureau : 1
message :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:239)  
  cairo_dock_preload_module_from_directory (/usr/lib/cairo-dock)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-clock.so' : (/lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.7' not found (required by /usr/lib/cairo-dock/libcd-clock.so))
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-cpusage.so' : (/lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.7' not found (required by /usr/lib/cairo-dock/libcd-cpusage.so))
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Tree)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Caroussel)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Simple)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Controler)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Mediaplayer)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_renderer:125)  
  cairo_dock_register_dialog_renderer (Text)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-gnome-integration.so' : (libgio-2.0.so.0: cannot open shared object file: No such file or directory)
message :  (cairo-dock-dock-factory.c:cairo_dock_create_new_dock:84)  
  cairo_dock_create_new_dock (_MainDock_)
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:201)  
  cairo_dock_set_renderer ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:945)  
  cairo_dock_update_conf_file_with_modules_full (/home/thomas/.config/cairo-dock/current_theme/cairo-dock.conf ; 0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_1)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_2)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/thomas/.config/cairo-dock/current_theme/cairo-dock.conf)
message :  (cairo-dock-dock-manager.c:cairo_dock_deactivate_temporary_auto_hide:525)  
  
message :  (cairo-dock-config.c:cairo_dock_read_conf_file:703)  
  g_cMainDockDefaultRendererName <- 3D plane
message :  (cairo-dock-config.c:cairo_dock_read_conf_file:853)  
   utilisation du repertoire local /home/thomas/.config/cairo-dock/current_theme/icons
cairo_dock_get_desklet_decoration (personnal)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (personnal)
debug   :  (cairo-dock-emblem.c:cairo_dock_get_emblem_path:237)  
  
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-config.c:cairo_dock_read_conf_file:1174)  
    g_fReflectSize : 22.85 pixels
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (1 / 20)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
  MaJ des decorations du fond -> 2.00x0.00
message :  (cairo-dock-dock-factory.c:cairo_dock_build_docks_tree_with_desktop_files:564)  
  cairo_dock_build_docks_tree_with_desktop_files (/home/thomas/.config/cairo-dock/current_theme/launchers)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01gnome-system-monitor.desktop
 we will assume that its class is 'gnome-system-monitor'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + System Monitor/gnome-system-monitor
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (gnome-system-monitor)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01evolution-mail.desktop
 we will assume that its class is 'evolution'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Evolution Mail/evolution
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (evolution)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01ccsm.desktop
 we will assume that its class is 'ccsm'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Compiz-Fusion/ccsm
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (ccsm)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Firefox Web Browser/firefox
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (firefox)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01ekiga.desktop
 we will assume that its class is 'ekiga'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Ekiga Softphone/ekiga
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (ekiga)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01totem.desktop
 we will assume that its class is 'totem'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Movie Player/totem
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (totem)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01f-spot.desktop
 we will assume that its class is 'f-spot'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + F-Spot Photo Manager/f-spot
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (f-spot)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01pidgin.desktop
 we will assume that its class is 'pidgin'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Pidgin Internet Messenger/pidgin
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (pidgin)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01nautilus.desktop
 we will assume that its class is 'nautilus'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + File Browser/nautilus
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (nautilus)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01ooo-writer.desktop
 we will assume that its class is 'ooffice'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + OpenOffice.org Word Processor/ooffice
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (ooffice)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01gnome-terminal.desktop
 we will assume that its class is 'gnome-terminal'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Terminal/gnome-terminal
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (gnome-terminal)
nouvelle icone d'appli (12582915)
nouvelle icone d'appli (33554446)
nouvelle icone d'appli (33554476)
nouvelle icone d'appli (33554481)
nouvelle icone d'appli (16777248)
nouvelle icone d'appli (48234648)
message :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:531)  
  recuperation de 'Ubuntu Forums - Search Results - Mozilla Firefox' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:539)  
    res_name : Navigator(814e128); res_class : Firefox(814e610)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:528)  
  cairo_dock_create_surface_from_class (firefox)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:532)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:541)  
    Firefox Web Browser
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:544)  
  Firefox Web Browser va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:194)  
  cairo_dock_add_appli_to_class (firefox)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1145)  
  cairo_dock_insert_appli_in_dock (Ubuntu Forums - Search Results - Mozilla Firefox, 48234648)
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:304)  
  
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:328)  
  >>> Firefox Web Browser prendra un indicateur au prochain redraw ! (Xid : 48234648)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1150)  
   -> se fait inhiber
nouvelle icone d'appli (50331680)
message :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:531)  
  recuperation de 'thomas@thomas-laptop: ~' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:539)  
    res_name : gnome-terminal(81504c8); res_class : Gnome-terminal(8148940)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:528)  
  cairo_dock_create_surface_from_class (gnome-terminal)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:532)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:541)  
    Terminal
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:544)  
  Terminal va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:194)  
  cairo_dock_add_appli_to_class (gnome-terminal)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1145)  
  cairo_dock_insert_appli_in_dock (thomas@thomas-laptop: ~, 50331680)
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:304)  
  
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:328)  
  >>> Terminal prendra un indicateur au prochain redraw ! (Xid : 50331680)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1150)  
   -> se fait inhiber
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:408)  
    cette fenetre est timide
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (terminal)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/thomas/.config/cairo-dock/current_theme/plug-ins/terminal/terminal.conf)
iRotation:0°
decorations : default
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:31)  
  cairo_dock_create_applet_surface (32.00x32.00 x 2.00 / 1)
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:40)  
   -> 64.00x64.00 x 2.00
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (terminal-init.c:init:34)  
  init (/home/thomas/.config/cairo-dock/current_theme/plug-ins/terminal/terminal.conf)

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
message :  (cairo-dock-dock-factory.c:cairo_dock_insert_icon_in_dock_full:717)  
  separateur necessaire
 insertion de terminal apres OpenOffice.org Word Processor -> iSeparatorType : 3
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 48.00x48.00
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (logout)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/thomas/.config/cairo-dock/current_theme/plug-ins/logout/logout.conf)
iRotation:0°
decorations : default
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:31)  
  cairo_dock_create_applet_surface (32.00x32.00 x 2.00 / 1)
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:40)  
   -> 64.00x64.00 x 2.00
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 64.00x64.00
message :  (applet-init.c:init:13)  
  init (/home/thomas/.config/cairo-dock/current_theme/plug-ins/logout/logout.conf)

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:201)  
  cairo_dock_set_renderer ((null))
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (1053 / 20)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:649)  
    -> changement du ratio : 1.000 -> 0.019 (0, 0 try)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (124 / 20)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:649)  
    -> changement du ratio : 0.019 -> 0.003 (0, 1 try)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (84 / 20)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:649)  
    -> changement du ratio : 0.003 -> 0.001 (0, 2 try)
debug   :  (cairo-dock-X-utilities.c:cairo_dock_set_strut_partial:182)  
  cairo_dock_set_strut_partial (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
debug   :  (cairo-dock-X-utilities.c:cairo_dock_set_xwindow_type_hint:200)  
  cairo_dock_set_xwindow_type_hint (52428804, _NET_WM_WINDOW_TYPE_DOCK=361)
message :  (cairo-dock-dock-manager.c:cairo_dock_search_max_decorations_size:192)  
    decorations max : 79x0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
  MaJ des decorations du fond -> 158.00x0.00
debug   :  (cairo-dock-dock-factory.c:cairo_dock_place_root_dock:877)  
  cairo_dock_place_root_dock (0, 0, 1)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_place_root_dock:890)  
   move to (387;1278)
cairo_dock_reload_desklets_decorations (0)
add personnal
add default
add personnal
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/thomas/.config/cairo-dock/current_theme/cairo-dock_easy.conf)
debug   :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:945)  
  cairo_dock_update_conf_file_with_modules_full (/home/thomas/.config/cairo-dock/current_theme/cairo-dock_easy.conf ; 0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_1)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_2)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/thomas/.config/cairo-dock/current_theme/cairo-dock_easy.conf)
cairo-dock: symbol lookup error: cairo-dock: undefined symbol: g_timeout_add_seconds
thomas@thomas-laptop:~$ 
```

Just out of curiosity, what should I do to find out if it is actually hiding or not?:confused:

Thanks.

---

### Post by fabounet on 2008-11-06
> cairo-dock: undefined symbol: g_timeout_add_seconds

means your glib is out if date
you need at least glib 2.10 or 2.12, dont remember.
so the easiest way is to install it from the sources(it has backward compatibility so you won't break your system)

---

### Post by thomasboleyn on 2008-11-06
> **fabounet said:**
> means your glib is out if date
you need at least glib 2.10 or 2.12, dont remember.
so the easiest way is to install it from the sources(it has backward compatibility so you won't break your system)

Ok, I've compiled glib 2.18 from sources, but the terminal debugging is still saying the same thing. Do I need to uninstall the old glib version synaptic finds? Or will that break something?:confused:

---

### Post by fabounet on 2008-11-07
you can probably uninstall the old version, but a better way is to install the new one in /usr/local (use ./configure --prefix=/usr/local)
, then when you compile the dock, do a export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
and PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH

---

### Post by thomasboleyn on 2008-11-07
> **fabounet said:**
> you can probably uninstall the old version, but a better way is to install the new one in /usr/local (use ./configure --prefix=/usr/local)
, then when you compile the dock, do a export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
and PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH

Ok, how do I do implement the second part, after './configure --prefix=/usr/local'?

Thanks.

---

### Post by thomasboleyn on 2008-11-08
Bump!

---

### Post by thomasboleyn on 2008-11-10
Anyone...?:confused:

---

### Post by fabounet on 2008-11-10
```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH
export PATH=/usr/local/bin:$PATH
autoreconf -isf
./configure --prefix=/usr/local
make
sudo make install

```

for the dock, the plug-ins, and the themes.
then launch your dock by cairo-dock -g in this terminal, or /usr/local/bin/cairo-dock -g otherwise.

---

