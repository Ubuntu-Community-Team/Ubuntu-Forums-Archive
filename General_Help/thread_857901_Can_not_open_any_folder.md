---
title: "Can not open any folder"
date: 2008-07-13
forum: General Help
---

### Post by getmemoney on 2008-07-13
Hi
I'm having a problem when I tried to open any folder. 
I click a folder from desktop, a window open and after that, I click another folder (or subfolder), all folder in my desktop disappear and the HOME folder open. And when I tried to to open a .deb file, the window open to load something and vanish (when it finished loading), nothing happen. I'm using Ubuntu 7.10 that has upgraded from 7.04 and some applications are compiz confuse and guarddog.

---

### Post by ghost_ryder35 on 2008-07-13
run nautilus in a terminal and post the errors that it logs to this thread.

```

nautilus

```

---

### Post by getmemoney on 2008-07-13
I ran "nautilus" command and I got the log:

```
===== BEGIN MILESTONES =====
0x8186a38 2008/07/13 11:42:59.6564 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8186a38 2008/07/13 11:42:59.6565 (USER): debug log dumped due to signal 6
===== END MILESTONES =====
===== BEGIN RING BUFFER =====
0x8186a38 2008/07/13 11:42:14.3586 (USER): window 0x8200838 open location: old="(none)", new="x-nautilus-desktop:"
0x8186a38 2008/07/13 11:42:14.4375 (USER): create new navigation window=0x81e4950
0x8186a38 2008/07/13 11:42:14.4375 (USER): window 0x81e4950 open location: old="(none)", new="file:///home/getmemoney"
0x8186a38 2008/07/13 11:42:14.9157 (USER): change view of window 0x81e4950: "file:///home/getmemoney" to "OAFIID:Nautilus_File_Manager_Icon_View"
0x8186a38 2008/07/13 11:42:15.3018 (USER): finished loading window 0x81e4950: file:///home/getmemoney
0x8186a38 2008/07/13 11:42:15.4101 (USER): finished loading window 0x8200838: x-nautilus-desktop:
0x8186a38 2008/07/13 11:42:56.6355 (USER): selection changed in window 0x8200838
	x-nautilus-desktop:///1.0%20GB%20Volume.volume
0x8186a38 2008/07/13 11:42:56.8106 (USER): fm_directory_view_activate_files window=0x8200838
	x-nautilus-desktop:///1.0%20GB%20Volume.volume
0x8186a38 2008/07/13 11:42:56.8126 (USER): directory view open_location window=0x8200838: file:///media/sda6
0x8186a38 2008/07/13 11:42:56.8126 (USER): window 0x8200838 open location: old="x-nautilus-desktop:", new="file:///media/sda6"
0x8186a38 2008/07/13 11:42:56.8608 (USER): create new navigation window=0x81e4c20
0x8186a38 2008/07/13 11:42:57.1362 (USER): change view of window 0x81e4c20: "file:///media/sda6" to "OAFIID:Nautilus_File_Manager_Icon_View"
0x8186a38 2008/07/13 11:42:57.5083 (USER): finished loading window 0x81e4c20: file:///media/sda6
0x8186a38 2008/07/13 11:42:59.3947 (USER): selection changed in window 0x81e4c20
	file:///media/sda6/mami%20%26%20's%20frs
0x8186a38 2008/07/13 11:42:59.5869 (USER): fm_directory_view_activate_files window=0x81e4c20
	file:///media/sda6/mami%20%26%20's%20frs
0x8186a38 2008/07/13 11:42:59.5873 (USER): directory view open_location window=0x81e4c20: file:///media/sda6/mami%20%26%20's%20frs
0x8186a38 2008/07/13 11:42:59.5873 (USER): window 0x81e4c20 open location: old="file:///media/sda6", new="file:///media/sda6/mami%20%26%20's%20frs"
0x8186a38 2008/07/13 11:42:59.5874 (USER): finished loading window 0x81e4c20: file:///media/sda6
0x8186a38 2008/07/13 11:42:59.6564 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8186a38 2008/07/13 11:42:59.6565 (USER): debug log dumped due to signal 6
===== END RING BUFFER =====


This configuration for the debug log can be re-created
by putting the following in ~/nautilus-debug-log.conf
(use ';' to separate domain names):


[debug log]
max lines=1000
```

---

