---
title: "pc switches off at login screen. Meerkat"
date: 2010-10-29
forum: Hardware
---

### Post by pdk on 2010-10-29
I recently installed meerkat alternate cd . Apart from using update manager I have not hacked anything.
I have an old pentium 4 with
display adapter via/s3g unichrome pro igp
via cpu to agp2.0/agp3.0 controller
When I switch on ( machine cold) I get to the meerkat login screen and the pc switches off.
I can happily boot to windows and work all day.
tail syslog
***************************************************************
** (process:1167): DEBUG: Greeter session pid=1167 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-9TQeao/database
gdm-simple-greeter[1167]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
****************************************************************From hwlist
*-display UNCLAIMED
                description: VGA compatible controller
                product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2

Any ideas ???
I have 2 other machines running fine they have different display controllers.
Peter

---

