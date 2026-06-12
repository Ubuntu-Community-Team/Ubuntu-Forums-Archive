---
title: "open office crashes on lucid trying to open Microsoft xls file"
date: 2010-05-11
forum: Hardware
---

### Post by sahoo on 2010-05-11
I just installed ubuntu 10.04. Now, I can't get open office to work. It crashes with following stack trace while trying to open a Microsoft xls file. It was working when I was on Ubuntu 9.04:

> terminate called after throwing an instance of 'com::sun::star::loader::CannotActivateFactoryException'
ss141213@Sahoo:/space/ss141213$ terminate called recursively


Fatal exception: Signal 6
Stack:
/usr/lib/openoffice/program/../basis-link/ure-link/lib/libuno_sal.so.3(+0x207c5)[0x4e07c5]
/usr/lib/openoffice/program/../basis-link/ure-link/lib/libuno_sal.so.3(+0x20918)[0x4e0918]
/usr/lib/openoffice/program/../basis-link/ure-link/lib/libuno_sal.so.3(+0x209b3)[0x4e09b3]
[0xa0a400]
/lib/tls/i686/cmov/libc.so.6(abort+0x182)[0x13da82]
/usr/lib/libstdc++.so.6(_ZN9__gnu_cxx27__verbose_terminate_handlerEv+0x52)[0x855432]
/usr/lib/libstdc++.so.6(+0xbd465)[0x853465]
/usr/lib/libstdc++.so.6(+0xbd4a2)[0x8534a2]
/usr/lib/libstdc++.so.6(+0xbd5e1)[0x8535e1]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(_ZN4cppu29loadSharedLibComponentFactoryERKN3rtl8OUStringES3_S3_RKN3com3sun4star3uno9ReferenceINS6_4lang20XMultiServiceFactoryEEERKNS8_INS6_8registry12XRegistryKeyEEE+0x720)[0x6e1980]
/usr/lib/ure/lib/bootstrap.uno.so(+0x5430c)[0x187830c]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4fe88)[0x6d3e88]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x50afa)[0x6d4afa]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4c3e0)[0x6d03e0]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4c6d3)[0x6d06d3]
/usr/lib/ure/lib/bootstrap.uno.so(+0x2b0e8)[0x184f0e8]
/usr/lib/ure/lib/bootstrap.uno.so(+0x25ad7)[0x1849ad7]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN3vcl9unohelper19CreateBreakIteratorEv+0x77)[0x7868667]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x15f505)[0x7916505]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x165107)[0x791c107]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN12OutputDevice8DrawTextERK9RectangleRK6StringtPN4_STL6vectorIS0_NS6_9allocatorIS0_EEEEPS3_+0x119)[0x791d0b9]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x2ead4a)[0x7aa1d4a]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN9FixedText5PaintERK9Rectangle+0x4d)[0x7aa1fcd]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x2954da)[0x7a4c4da]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x295229)[0x7a4c229]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x295229)[0x7a4c229]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x2956e0)[0x7a4c6e0]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x295741)[0x7a4c741]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN5Timer7TimeoutEv+0x1c)[0x786681c]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN5Timer21ImplTimerCallbackProcEv+0x7e)[0x7866e3e]
/usr/lib/openoffice/basis3.2/program/libvclplug_genli.so(_ZNK10X11SalData7TimeoutEv+0x2a)[0x16f408a]
/usr/lib/openoffice/basis3.2/program/libvclplug_gtkli.so(+0x12896)[0x1f01896]
/lib/libglib-2.0.so.0(+0x3bd5c)[0x15c3d5c]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0x15c35e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0x15c72d8]
/lib/libglib-2.0.so.0(g_main_context_iteration+0x68)[0x15c74b8]
/usr/lib/openoffice/basis3.2/program/libvclplug_gtkli.so(+0x12648)[0x1f01648]
/usr/lib/openoffice/basis3.2/program/libvclplug_genli.so(_ZN14X11SalInstance5YieldEbb+0x37)[0x1702107]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN11Application5YieldEb+0x5e)[0x7860b0e]
/usr/lib/openoffice/program/../basis-link/program/libsvxli.so(+0x12dc24)[0x30fac24]
/usr/lib/openoffice/program/../basis-link/program/libsvxli.so(+0x125dcc)[0x30f2dcc]
/usr/lib/openoffice/program/../basis-link/program/libsvxli.so(+0x21a5e5)[0x31e75e5]
/usr/lib/openoffice/program/../basis-link/program/libsvxli.so(+0x21c06b)[0x31e906b]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x17dfa)[0x2acdfa]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x184fe)[0x2ad4fe]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x1873c)[0x2ad73c]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0xae3de)[0x78653de]
/usr/lib/openoffice/program/../basis-link/program/libvos3gcc3.so(_ZN3vos26signalHandlerFunction_implEPvP13oslSignalInfo+0x18)[0x453cc8]
/usr/lib/openoffice/program/../basis-link/ure-link/lib/libuno_sal.so.3(+0x2098b)[0x4e098b]
[0xa0a400]
/lib/tls/i686/cmov/libc.so.6(abort+0x182)[0x13da82]
/usr/lib/libstdc++.so.6(_ZN9__gnu_cxx27__verbose_terminate_handlerEv+0x14f)[0x85552f]
/usr/lib/libstdc++.so.6(+0xbd465)[0x853465]
/usr/lib/libstdc++.so.6(+0xbd4a2)[0x8534a2]
/usr/lib/libstdc++.so.6(+0xbd5e1)[0x8535e1]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(_ZN4cppu29loadSharedLibComponentFactoryERKN3rtl8OUStringES3_S3_RKN3com3sun4star3uno9ReferenceINS6_4lang20XMultiServiceFactoryEEERKNS8_INS6_8registry12XRegistryKeyEEE+0x720)[0x6e1980]
/usr/lib/ure/lib/bootstrap.uno.so(+0x5430c)[0x187830c]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4fe88)[0x6d3e88]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x50afa)[0x6d4afa]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4c3e0)[0x6d03e0]
/usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3(+0x4c6d3)[0x6d06d3]
/usr/lib/ure/lib/bootstrap.uno.so(+0x2b0e8)[0x184f0e8]
/usr/lib/ure/lib/bootstrap.uno.so(+0x25ad7)[0x1849ad7]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x27ef1d)[0xb26d4f1d]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x27232d)[0xb26c832d]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x272ceb)[0xb26c8ceb]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x28db4b)[0xb26e3b4b]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x28e23f)[0xb26e423f]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(+0x28e2e7)[0xb26e42e7]
/usr/lib/openoffice/program/../basis-link/program/libsvxcoreli.so(_ZN10EditEngine16CreateTextObjectEv+0x20)[0xb269ef10]
/usr/lib/openoffice/program/../basis-link/program/libscli.so(+0x5da6f7)[0xb332c6f7]
/usr/lib/openoffice/program/../basis-link/program/libscli.so(_ZN10ScDocShell7InitNewERKN3com3sun4star3uno9ReferenceINS2_5embed8XStorageEEE+0xd6)[0xb2ea6076]
/usr/lib/openoffice/program/../basis-link/program/libsfxli.so(_ZN14SfxObjectShell6DoLoadEP9SfxMedium+0xcbd)[0xfce63d]
/usr/lib/openoffice/program/../basis-link/program/libsfxli.so(_ZN12SfxBaseModel4loadERKN3com3sun4star3uno8SequenceINS2_5beans13PropertyValueEEE+0x1b0)[0x1025bf0]
/usr/lib/openoffice/program/../basis-link/program/libsfxli.so(+0x254071)[0x109f071]
/usr/lib/openoffice/program/../basis-link/program/libfwkli.so(+0x144cfa)[0x24e3cfa]
/usr/lib/openoffice/program/../basis-link/program/libfwkli.so(+0x1454b6)[0x24e44b6]
/usr/lib/openoffice/program/../basis-link/program/libfwkli.so(+0x1378d1)[0x24d68d1]
/usr/lib/openoffice/program/../basis-link/program/libfwkli.so(+0x138021)[0x24d7021]
/usr/lib/openoffice/program/../basis-link/program/libcomphelp4gcc3.so(_ZN10comphelper19SynchronousDispatch8dispatchERKN3com3sun4star3uno9ReferenceINS4_10XInterfaceEEERKN3rtl8OUStringESD_lRKNS4_8SequenceINS3_5beans13PropertyValueEEE+0x3b9)[0xdbbf79]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x3c8b2)[0x2d18b2]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x509ae)[0x2e59ae]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x26ac8)[0x2bbac8]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x28b0a)[0x2bdb0a]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x28c24)[0x2bdc24]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0x2ac001)[0x7a63001]
/usr/lib/openoffice/basis3.2/program/libvclplug_genli.so(_ZN10SalDisplay21DispatchInternalEventEv+0xa3)[0x16f7683]
/usr/lib/openoffice/basis3.2/program/libvclplug_gtkli.so(+0x124c2)[0x1f014c2]
/lib/libglib-2.0.so.0(+0x39661)[0x15c1661]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0x15c35e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0x15c72d8]
/lib/libglib-2.0.so.0(g_main_context_iteration+0x68)[0x15c74b8]
/usr/lib/openoffice/basis3.2/program/libvclplug_gtkli.so(+0x12648)[0x1f01648]
/usr/lib/openoffice/basis3.2/program/libvclplug_genli.so(_ZN14X11SalInstance5YieldEbb+0x37)[0x1702107]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN11Application5YieldEb+0x5e)[0x7860b0e]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_ZN11Application7ExecuteEv+0x3c)[0x7860b8c]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(+0x226c8)[0x2b76c8]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(+0xaf3ba)[0x78663ba]
/usr/lib/openoffice/program/../basis-link/program/libvclli.so(_Z6SVMainv+0x35)[0x78664b5]
/usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so(soffice_main+0xaf)[0x2efabf]
/usr/lib/openoffice/program/soffice.bin(main+0x21)[0x8048da1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126bd6]
/usr/lib/openoffice/program/soffice.bin[0x8048ce1]

--
uname -a output is given below:
Linux Sahoo 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

### Post by Hagar Delest on 2010-05-13
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

