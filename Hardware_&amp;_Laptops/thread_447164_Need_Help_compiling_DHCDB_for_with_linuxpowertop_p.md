---
title: "Need Help compiling DHCDB for with linuxpowertop patches"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by extremecarver on 2007-05-17
Hi, after patching dhcdbd I get the following long error list when I enter "make" - there is no howto in the source for compiling so I don't know any other way to do it - below is the log - if someone knows what to do that would be great

```
root@felix-laptop:/home/felix/Desktop/DHCDBD/dhcdbd-2.0# bzip2 -dc '/home/felix/Desktop/DHCDBD/patch1.bz2'  | patch -p1
patching file debian/dhcdbd.postinst
patching file debian/dhcdbd.manpages
patching file debian/control
patching file debian/dhcdbd.docs
patching file debian/rules
patching file debian/watch
patching file debian/dhcdbd.postrm
patching file debian/changelog
patching file debian/compat
patching file debian/patches/40-dbus-connection.patch
patching file debian/patches/03-remove_extended_options_from_dhcdbd.patch
patching file debian/patches/02-dhcdbd_location.patch
patching file debian/patches/30-pid-file-mode.patch
patching file debian/patches/01-debian_specific_paths.patch
patching file debian/copyright
patching file debian/dhcdbd.dhcp3
patching file debian/dhcdbd.prerm
patching file debian/dhcdbd.dbus-event
patching file debian/dhcdbd.1
patching file debian/dhcdbd.preinst
root@felix-laptop:/home/felix/Desktop/DHCDBD/dhcdbd-2.0# bzip2 -dc '/home/felix/Desktop/DHCDBD/patch2.bz2'  | patch -p1
patching file src/dbus_service.c
root@felix-laptop:/home/felix/Desktop/DHCDBD/dhcdbd-2.0# make oldconfig
make: *** No rule to make target `oldconfig'.  Stop.
root@felix-laptop:/home/felix/Desktop/DHCDBD/dhcdbd-2.0# make xconfig
make: *** No rule to make target `xconfig'.  Stop.
root@felix-laptop:/home/felix/Desktop/DHCDBD/dhcdbd-2.0# make
make -C src
Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
make[1]: Entering directory `/home/felix/Desktop/DHCDBD/dhcdbd-2.0/src'
cc -g -Wall  -DDBUS_API_SUBJECT_TO_CHANGE -D_GNU_SOURCE -I../include  -c dbus_service.c
dbus_service.c:29:23: error: dbus/dbus.h: No such file or directory
dbus_service.c:36: error: expected specifier-qualifier-list before ‘DBusConnection’
dbus_service.c:81: error: expected specifier-qualifier-list before ‘DBusTimeout’
dbus_service.c:108: error: expected ‘)’ before ‘*’ token
dbus_service.c:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_handler’
dbus_service.c: In function ‘dbus_svc_add_path_handler’:
dbus_service.c:231: error: ‘DBusObjectPathVTable’ undeclared (first use in this function)
dbus_service.c:231: error: (Each undeclared identifier is reported only once
dbus_service.c:231: error: for each function it appears in.)
dbus_service.c:231: error: expected ‘;’ before ‘vtable’
dbus_service.c:236: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:237: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:245: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:246: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:252: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:253: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:269: warning: implicit declaration of function ‘dbus_connection_register_object_path’
dbus_service.c:269: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:270: error: ‘vtable’ undeclared (first use in this function)
dbus_service.c:271: warning: implicit declaration of function ‘dbus_connection_register_fallback’
dbus_service.c:271: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:274: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:275: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:279: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c: In function ‘dbus_svc_remove_path_handler’:
dbus_service.c:295: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:296: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:302: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c:305: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:306: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:310: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c:312: warning: implicit declaration of function ‘dbus_connection_unregister_object_path’
dbus_service.c:312: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:313: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:314: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c: In function ‘add_handler’:
dbus_service.c:336: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:337: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c: In function ‘find_root’:
dbus_service.c:360: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c: In function ‘dbus_svc_add_handler’:
dbus_service.c:375: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:376: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:384: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:385: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:390: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:393: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:400: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:406: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c: In function ‘dbus_svc_remove_handler’:
dbus_service.c:419: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:420: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c: In function ‘filter_current_message’:
dbus_service.c:453: error: ‘DBusConnectionState’ has no member named ‘rejectMessage’
dbus_service.c:456: error: ‘DBusMessage’ undeclared (first use in this function)
dbus_service.c:456: error: ‘message’ undeclared (first use in this function)
dbus_service.c:456: error: ‘DBusConnectionState’ has no member named ‘currentMessage’
dbus_service.c:457: warning: implicit declaration of function ‘dbus_message_get_type’
dbus_service.c:458: warning: implicit declaration of function ‘dbus_message_get_serial’
dbus_service.c:459: warning: implicit declaration of function ‘dbus_message_get_no_reply’
dbus_service.c:460: warning: implicit declaration of function ‘dbus_message_get_path’
dbus_service.c:461: warning: implicit declaration of function ‘dbus_message_get_destination’
dbus_service.c:462: warning: implicit declaration of function ‘dbus_message_get_member’
dbus_service.c:463: warning: implicit declaration of function ‘dbus_message_get_interface’
dbus_service.c:464: warning: implicit declaration of function ‘dbus_message_get_sender’
dbus_service.c:465: warning: implicit declaration of function ‘dbus_message_get_signature’
dbus_service.c:468: error: ‘DBusConnectionState’ has no member named ‘rejectMessage’
dbus_service.c: At top level:
dbus_service.c:474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_filter’
dbus_service.c: In function ‘dbus_svc_add_message_filter’:
dbus_service.c:498: error: ‘DBusError’ undeclared (first use in this function)
dbus_service.c:498: error: expected ‘;’ before ‘error’
dbus_service.c:503: warning: implicit declaration of function ‘dbus_connection_add_filter’
dbus_service.c:503: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:503: error: ‘message_filter’ undeclared (first use in this function)
dbus_service.c:504: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:505: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:512: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:513: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:523: error: ‘error’ undeclared (first use in this function)
dbus_service.c:524: warning: implicit declaration of function ‘dbus_error_init’
dbus_service.c:528: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:529: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:538: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:539: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:545: warning: implicit declaration of function ‘dbus_bus_add_match’
dbus_service.c:545: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:547: warning: implicit declaration of function ‘dbus_error_is_set’
dbus_service.c:548: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:549: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:560: error: ‘DBusConnectionState’ has no member named ‘filters’
dbus_service.c: In function ‘dbus_svc_remove_message_filter’:
dbus_service.c:565: error: ‘DBusConnectionState’ has no member named ‘filters’
dbus_service.c:567: error: ‘DBusError’ undeclared (first use in this function)
dbus_service.c:567: error: expected ‘;’ before ‘error’
dbus_service.c:571: error: ‘DBusConnectionState’ has no member named ‘filters’
dbus_service.c:574: error: ‘error’ undeclared (first use in this function)
dbus_service.c:578: warning: implicit declaration of function ‘dbus_bus_remove_match’
dbus_service.c:578: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:583: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:584: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:594: error: ‘DBusConnectionState’ has no member named ‘filters’
dbus_service.c:595: warning: implicit declaration of function ‘dbus_connection_remove_filter’
dbus_service.c:595: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:595: error: ‘message_filter’ undeclared (first use in this function)
dbus_service.c: At top level:
dbus_service.c:600: error: expected declaration specifiers or ‘...’ before ‘DBusMessage’
dbus_service.c:601: error: conflicting types for ‘dbus_svc_get_args_va’
../include/dbus_service.h:207: error: previous declaration of ‘dbus_svc_get_args_va’ was here
dbus_service.c: In function ‘dbus_svc_get_args_va’:
dbus_service.c:602: error: ‘DBusError’ undeclared (first use in this function)
dbus_service.c:602: error: expected ‘;’ before ‘error’
dbus_service.c:604: error: ‘error’ undeclared (first use in this function)
dbus_service.c:607: warning: implicit declaration of function ‘dbus_message_get_args_valist’
dbus_service.c:607: error: ‘msg’ undeclared (first use in this function)
dbus_service.c:610: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:611: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:612: warning: implicit declaration of function ‘dbus_error_free’
dbus_service.c:613: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:614: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c: At top level:
dbus_service.c:623: error: expected declaration specifiers or ‘...’ before ‘DBusMessage’
dbus_service.c:624: error: conflicting types for ‘dbus_svc_get_args’
../include/dbus_service.h:201: error: previous declaration of ‘dbus_svc_get_args’ was here
dbus_service.c: In function ‘dbus_svc_get_args’:
dbus_service.c:629: error: ‘msg’ undeclared (first use in this function)
dbus_service.c:629: error: incompatible type for argument 3 of ‘dbus_svc_get_args_va’
dbus_service.c:629: error: too many arguments to function ‘dbus_svc_get_args_va’
dbus_service.c: In function ‘dbus_svc_send_va’:
dbus_service.c:640: error: ‘DBusMessageIter’ undeclared (first use in this function)
dbus_service.c:640: error: expected ‘;’ before ‘iter’
dbus_service.c:642: error: ‘DBusMessage’ undeclared (first use in this function)
dbus_service.c:642: error: ‘msg’ undeclared (first use in this function)
dbus_service.c:647: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:648: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:652: error: ‘DBUS_MESSAGE_TYPE_ERROR’ undeclared (first use in this function)
dbus_service.c:653: warning: implicit declaration of function ‘dbus_message_append_args_valist’
dbus_service.c:654: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:655: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:659: error: ‘DBUS_TYPE_STRING’ undeclared (first use in this function)
dbus_service.c:663: warning: implicit declaration of function ‘dbus_message_set_error_name’
dbus_service.c:664: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:665: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:676: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:677: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:681: warning: implicit declaration of function ‘dbus_message_iter_init_append’
dbus_service.c:681: error: ‘iter’ undeclared (first use in this function)
dbus_service.c:683: warning: implicit declaration of function ‘dbus_message_iter_append_basic’
dbus_service.c:684: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:685: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:690: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:691: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:696: warning: implicit declaration of function ‘dbus_connection_send’
dbus_service.c:696: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:697: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:698: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:702: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:703: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:705: warning: implicit declaration of function ‘dbus_connection_flush’
dbus_service.c:705: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c: In function ‘dbus_svc_new_message’:
dbus_service.c:729: error: ‘DBusMessage’ undeclared (first use in this function)
dbus_service.c:729: error: ‘msg’ undeclared (first use in this function)
dbus_service.c:729: warning: implicit declaration of function ‘dbus_message_new’
dbus_service.c:732: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:733: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:738: warning: implicit declaration of function ‘dbus_message_set_reply_serial’
dbus_service.c:739: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:740: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:745: warning: implicit declaration of function ‘dbus_message_set_destination’
dbus_service.c:746: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:747: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:751: warning: implicit declaration of function ‘dbus_message_set_path’
dbus_service.c:752: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:753: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:757: warning: implicit declaration of function ‘dbus_message_set_interface’
dbus_service.c:758: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:759: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:763: warning: implicit declaration of function ‘dbus_message_set_member’
dbus_service.c:764: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:765: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:770: warning: control reaches end of non-void function
dbus_service.c: In function ‘dbus_svc_send_message’:
dbus_service.c:775: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:776: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:777: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:781: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:782: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:784: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c: In function ‘dbus_svc_message_append_args’:
dbus_service.c:796: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c:797: error: ‘struct dbcs_s’ has no member named ‘eh’
dbus_service.c: In function ‘dbus_svc_call’:
dbus_service.c:810: error: ‘DBusMessage’ undeclared (first use in this function)
dbus_service.c:810: error: ‘message’ undeclared (first use in this function)
dbus_service.c:810: error: ‘reply’ undeclared (first use in this function)
dbus_service.c:810: warning: left-hand operand of comma expression has no effect
dbus_service.c:812: error: ‘DBusError’ undeclared (first use in this function)
dbus_service.c:812: error: expected ‘;’ before ‘error’
dbus_service.c:817: error: ‘error’ undeclared (first use in this function)
dbus_service.c:820: warning: implicit declaration of function ‘dbus_message_new_method_call’
dbus_service.c:823: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:824: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:831: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:832: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:838: warning: implicit declaration of function ‘dbus_connection_send_with_reply_and_block’
dbus_service.c:838: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:841: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:842: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:849: warning: control reaches end of non-void function
dbus_service.c: At top level:
dbus_service.c:851: error: expected ‘)’ before ‘*’ token
dbus_service.c:863: error: expected ‘)’ before ‘*’ token
dbus_service.c:882: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘add_timeout’
dbus_service.c:902: error: expected ‘)’ before ‘*’ token
dbus_service.c:920: error: expected ‘)’ before ‘*’ token
dbus_service.c: In function ‘process_timeout’:
dbus_service.c:950: error: ‘DBusConnectionTimeout’ has no member named ‘cs’
dbus_service.c:952: warning: implicit declaration of function ‘dbus_timeout_get_enabled’
dbus_service.c:952: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:955: warning: implicit declaration of function ‘dbus_timeout_get_data’
dbus_service.c:955: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:955: warning: assignment makes pointer from integer without a cast
dbus_service.c:956: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c:956: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c:959: warning: implicit declaration of function ‘dbus_timeout_get_interval’
dbus_service.c:959: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:963: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:964: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:964: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:966: warning: implicit declaration of function ‘dbus_timeout_handle’
dbus_service.c:966: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:967: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c:970: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c: In function ‘process_timeouts’:
dbus_service.c:976: error: ‘DBusConnectionState’ has no member named ‘timeouts’
dbus_service.c: In function ‘find_timeout’:
dbus_service.c:992: error: ‘DBusConnectionTimeout’ has no member named ‘cs’
dbus_service.c:994: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:997: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c:997: warning: assignment makes pointer from integer without a cast
dbus_service.c:998: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c:998: error: ‘DBusConnectionTimeout’ has no member named ‘tv’
dbus_service.c:1001: error: ‘DBusConnectionTimeout’ has no member named ‘to’
dbus_service.c: In function ‘find_next_timeout’:
dbus_service.c:1015: error: ‘DBusConnectionState’ has no member named ‘timeouts’
dbus_service.c: At top level:
dbus_service.c:1024: error: expected ‘)’ before ‘*’ token
dbus_service.c:1053: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘add_watch’
dbus_service.c:1073: error: expected ‘)’ before ‘*’ token
dbus_service.c:1090: error: expected ‘)’ before ‘*’ token
dbus_service.c: In function ‘process_watch’:
dbus_service.c:1101: error: ‘DBusWatch’ undeclared (first use in this function)
dbus_service.c:1101: error: ‘w’ undeclared (first use in this function)
dbus_service.c:1107: error: expected expression before ‘)’ token
dbus_service.c:1108: warning: implicit declaration of function ‘dbus_watch_get_data’
dbus_service.c:1108: warning: assignment makes pointer from integer without a cast
dbus_service.c:1113: warning: implicit declaration of function ‘dbus_watch_get_enabled’
dbus_service.c:1116: warning: implicit declaration of function ‘dbus_watch_get_fd’
dbus_service.c:1117: warning: implicit declaration of function ‘dbus_watch_get_flags’
dbus_service.c:1119: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:1120: error: ‘DBusConnectionState’ has no member named ‘dh’
dbus_service.c:1122: error: ‘DBUS_WATCH_READABLE’ undeclared (first use in this function)
dbus_service.c:1122: error: ‘DBusConnectionState’ has no member named ‘s_r_fds’
dbus_service.c:1123: warning: implicit declaration of function ‘dbus_watch_handle’
dbus_service.c:1125: error: ‘DBUS_WATCH_WRITABLE’ undeclared (first use in this function)
dbus_service.c:1125: error: ‘DBusConnectionState’ has no member named ‘s_w_fds’
dbus_service.c:1128: error: ‘DBUS_WATCH_ERROR’ undeclared (first use in this function)
dbus_service.c:1128: error: ‘DBusConnectionState’ has no member named ‘s_e_fds’
dbus_service.c: In function ‘process_watches’:
dbus_service.c:1134: error: ‘DBusConnectionState’ has no member named ‘watches’
dbus_service.c: At top level:
dbus_service.c:1137: error: expected ‘)’ before ‘*’ token
dbus_service.c:1143: error: expected ‘)’ before ‘*’ token
dbus_service.c: In function ‘dbus_svc_main_loop’:
dbus_service.c:1190: error: ‘DBusConnectionState’ has no member named ‘status’
dbus_service.c:1191: error: ‘DBusConnectionState’ has no member named ‘s_r_fds’
dbus_service.c:1191: error: ‘DBusConnectionState’ has no member named ‘r_fds’
dbus_service.c:1192: error: ‘DBusConnectionState’ has no member named ‘s_w_fds’
dbus_service.c:1192: error: ‘DBusConnectionState’ has no member named ‘w_fds’
dbus_service.c:1193: error: ‘DBusConnectionState’ has no member named ‘s_e_fds’
dbus_service.c:1193: error: ‘DBusConnectionState’ has no member named ‘e_fds’
dbus_service.c:1195: error: ‘DBusConnectionState’ has no member named ‘n’
dbus_service.c:1195: error: ‘DBusConnectionState’ has no member named ‘s_r_fds’
dbus_service.c:1195: error: ‘DBusConnectionState’ has no member named ‘s_w_fds’
dbus_service.c:1196: error: ‘DBusConnectionState’ has no member named ‘s_e_fds’
dbus_service.c:1198: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1199: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1210: error: ‘DBusConnectionState’ has no member named ‘dispatchStatus’
dbus_service.c:1210: error: ‘DBUS_DISPATCH_COMPLETE’ undeclared (first use in this function)
dbus_service.c:1211: warning: implicit declaration of function ‘dbus_connection_dispatch’
dbus_service.c:1211: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c: In function ‘dbus_svc_quit’:
dbus_service.c:1219: error: ‘DBusConnectionState’ has no member named ‘status’
dbus_service.c: In function ‘dbus_svc_init’:
dbus_service.c:1223: error: ‘DBusConnection’ undeclared (first use in this function)
dbus_service.c:1223: error: ‘connection’ undeclared (first use in this function)
dbus_service.c:1224: error: ‘DBusError’ undeclared (first use in this function)
dbus_service.c:1224: error: expected ‘;’ before ‘error’
dbus_service.c:1227: error: ‘error’ undeclared (first use in this function)
dbus_service.c:1231: warning: implicit declaration of function ‘dbus_bus_get’
dbus_service.c:1236: warning: implicit declaration of function ‘dbus_connection_set_exit_on_disconnect’
dbus_service.c:1236: error: ‘FALSE’ undeclared (first use in this function)
dbus_service.c:1238: warning: implicit declaration of function ‘connection_setup’
dbus_service.c:1238: warning: assignment makes pointer from integer without a cast
dbus_service.c:1246: warning: implicit declaration of function ‘dbus_bus_request_name’
dbus_service.c:1247: error: ‘DBUS_REQUEST_NAME_REPLY_PRIMARY_OWNER’ undeclared (first use in this function)
dbus_service.c:1249: error: ‘DBUS_REQUEST_NAME_REPLY_EXISTS’ undeclared (first use in this function)
dbus_service.c:1250: error: ‘DBUS_REQUEST_NAME_REPLY_IN_QUEUE’ undeclared (first use in this function)
dbus_service.c:1251: error: ‘DBUS_REQUEST_NAME_REPLY_ALREADY_OWNER’ undeclared (first use in this function)
dbus_service.c:1262: warning: implicit declaration of function ‘dbus_connection_close’
dbus_service.c:1263: warning: implicit declaration of function ‘dbus_shutdown’
dbus_service.c: In function ‘dbus_svc_shutdown’:
dbus_service.c:1279: warning: implicit declaration of function ‘dbus_connection_set_watch_functions’
dbus_service.c:1279: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:1280: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1281: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1283: warning: implicit declaration of function ‘dbus_connection_set_timeout_functions’
dbus_service.c:1283: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:1284: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1285: error: ‘DBusConnectionState’ has no member named ‘eh’
dbus_service.c:1287: warning: implicit declaration of function ‘dbus_connection_set_dispatch_status_function’
dbus_service.c:1287: error: ‘DBusConnectionState’ has no member named ‘connection’
dbus_service.c:1289: error: ‘DBusConnectionState’ has no member named ‘timeouts’
dbus_service.c:1290: error: ‘DBusConnectionState’ has no member named ‘timeouts’
dbus_service.c:1291: error: ‘DBusConnectionState’ has no member named ‘watches’
dbus_service.c:1292: error: ‘DBusConnectionState’ has no member named ‘watches’
dbus_service.c:1293: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c:1294: error: ‘DBusConnectionState’ has no member named ‘roots’
dbus_service.c:1296: error: ‘DBusConnectionState’ has no member named ‘connection’
make[1]: *** [dbus_service.o] Error 1
make[1]: Leaving directory `/home/felix/Desktop/DHCDBD/dhcdbd-2.0/src'
make: *** [dhcdbd] Error 2

```

---

