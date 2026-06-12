---
title: "assertion failure"
date: 2008-11-03
forum: General Help
---

### Post by dracayr on 2008-11-03
hi,

when I try to play regnum online, it works fine, until I get to the places where there are many polys. then, I get lags (which is normal), and the program closes, and I get this error: ```
game: i830_vtbl.c:555: i830_emit_state: Assertion `get_dirty(state) == 0' failed.
Saving backtrace to crash_backtrace_19526.log
Got SIGABRT (aborted)
``` This is the first time I try to play regnum since a long time. But, when I last played it, it worked on the same machine under hardy (I have ibex now).
Well, I downloaded the mesa source and looked in the i830_vtbl.c file. I read about some fix with changing all the 'assert's in the file to 'ASSERT'. That didn't work though. I tried changing the asserts concerning get_dirty(state) so that they are always [FONT="Times New Roman"]true[/FONT] (in both the i830_vtbl.c *and* the i915_vtbl.c files). I compiled and installed. Restarted X. I tried to play the game again, but strangely it *still gives me the same error!* even though There is no occurence of an assertion that has something to do with get_dirty(state)!

the crash_backtrace:
```
libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x79) [0xb7deb4c9]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x1b) [0xb7debb7b]
[0xb7ff1400]
[0xb7ff1430]
/lib/tls/i686/cmov/libc.so.6(gsignal+0x50) [0xb706e880]
/lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7070248]
/lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb706772e]
/usr/lib/dri/i915_dri.so [0xb6ba735c]
/usr/lib/dri/i915_dri.so [0xb6bce1fc]
/usr/lib/dri/i915_dri.so [0xb6c77b89]
/usr/lib/dri/i915_dri.so(_tnl_run_pipeline+0x164) [0xb6c6ef14]
/usr/lib/dri/i915_dri.so [0xb6bcfc39]
/usr/lib/dri/i915_dri.so(_tnl_draw_prims+0x495) [0xb6c6f485]
/usr/lib/dri/i915_dri.so [0xb6c67cf0]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL22render_surface_elementEPNS_14SurfaceElementEPNS_19RenderingParametersE+0xaf8) [0xb778cb18]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL11render_meshEPNS_4MeshEP8Matrix4D+0xc8) [0xb775fa48]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL15render_gui_meshEffPNS_4MeshEPKSt6vectorI10BitmapBaseSaIS4_EEPKS3_I13StringElementSaIS9_EEf+0x15b) [0xb775f73b]
libs/libgui_extension.so(_ZN3GUI16Drawable_GUIMesh15render_internalEv+0xec) [0xb7a142bc]
libs/libgui.so(_ZN3GUI8Drawable6renderEv+0x38) [0xb7ae1538]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x112) [0xb7aba0b2]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x171) [0xb7aba111]
libs/libgui.so(_ZN3GUI6Widget11draw_signalEv+0x81) [0xb7aba471]
libs/libcommon_entities.so(_ZN13DisplayEntity15show_next_frameEv+0x57) [0xb7c4f987]
libs/libregnum_client.so(_ZN10GameClient7iterateEv+0x4c) [0xb7f6975c]
libs/libcore_client.so(_ZN8MainLoop7iterateEv+0x24) [0xb7dfd2e4]
./game(main+0x277) [0x8048f97]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7059685]
./game(__gxx_personality_v0+0x65) [0x8048c21]
```

dracayr

---

### Post by dracayr on 2008-11-04
OK, figured it out: the fix I tried worked (either changing the 'assert's to 'ASSERT', or making them always true), but the files didn't install in /usr/lib (only in /usr/local/lib), although I did 'make install'. Installed them manually now, and problem is fixed :)

dracayr

---

