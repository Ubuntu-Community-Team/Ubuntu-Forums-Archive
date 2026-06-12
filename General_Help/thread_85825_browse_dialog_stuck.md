---
title: "browse dialog stuck"
date: 2005-11-03
forum: General Help
---

### Post by kroiz on 2005-11-03
Hi,

I first noticed it in Anjuta, the browse dialog in the wizard cause the application to freeze when clicking its OK button.
I thought it is a bug, until I noticed that the same thing happen with meld with the same dialog(browse). I thougth that maybe it is a bug in the gnome framework (maybr gtk?). 
so I looked for other applications that use this dialog, I found that dialog also in the ScreenSaver advance dialog but there it did not stuck.
so Im stuck.
anyone has any ideas on how to get to the buttom of this?

---

### Post by kroiz on 2005-11-04
ppl please.
any idea on logs I could check?

I attaced a gdb to the stuck Anjuta and got this:
```
(gdb) where
#0  0xffffe410 in ?? ()
#1  0xbf83e9d0 in ?? ()
#2  0x00000002 in ?? ()
#3  0x00000000 in ?? ()
#4  0x43907bfe in pthread_setcanceltype () from /lib/tls/i686/cmov/libc.so.6
#5  0x438bdf9c in fork () from /lib/tls/i686/cmov/libc.so.6
#6  0x43a895b4 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x4be80463 in libgnomeui_module_info_get () from /usr/lib/libgnomeui-2.so.0
#8  <signal handler called>
#9  0xffffe410 in ?? ()
#10 0xbf83ee34 in ?? ()
#11 0x00000006 in ?? ()
#12 0x00002598 in ?? ()
#13 0x4385a9b1 in raise () from /lib/tls/i686/cmov/libc.so.6
#14 0x4385c2c9 in abort () from /lib/tls/i686/cmov/libc.so.6
#15 0x4388e6ea in __fsetlocking () from /lib/tls/i686/cmov/libc.so.6
#16 0x43894f54 in malloc_trim () from /lib/tls/i686/cmov/libc.so.6
#17 0x438952ca in free () from /lib/tls/i686/cmov/libc.so.6
#18 0x43ad7054 in g_free () from /usr/lib/libglib-2.0.so.0
#19 0x4be63550 in gnome_file_entry_get_type () from /usr/lib/libgnomeui-2.so.0
#20 0x43b4cab3 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#21 0x43b413a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#22 0x43b4fb13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#23 0x43b51150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#24 0x43b514c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#25 0x43d0922c in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#26 0x43d0aa4c in _gtk_button_set_depressed ()
   from /usr/lib/libgtk-x11-2.0.so.0
#27 0x43b4cab3 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#28 0x43b40d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#29 0x43b413a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#30 0x43b4f769 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#31 0x43b51150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#32 0x43b514c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#33 0x43d091a6 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#34 0x43d0a115 in _gtk_button_paint () from /usr/lib/libgtk-x11-2.0.so.0
#35 0x43dca02c in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#36 0x43b40d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#37 0x43b413a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#38 0x43b4fc9f in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#39 0x43b50ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#40 0x43b514c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#41 0x43eac16f in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#42 0x43dc8767 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#43 0x43dc8ba0 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#44 0x44047b2d in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#45 0x43ad04ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#46 0x43ad34f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#47 0x43ad37e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#48 0x43dc7e65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x080bda08 in main ()

```

somthing seems to be wrong after function number 4.

---

