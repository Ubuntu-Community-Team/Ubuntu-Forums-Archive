---
title: "Chrome - Can't enable hardware acceleration with Nvidia card and proprietary drivers"
date: 2015-08-25
forum: Hardware
---

### Post by chris408 on 2015-08-25
Usually I can figure this stuff out by searching other Linux forums but after spending an hour this one has me stumped.

When I go to chrome://gpu/ this is what I see:

```
[I]Software only, hardware acceleration unavailable

GPU process was unable to boot: GPU access is disabled in chrome://settings.
Disabled Features: all
[/I]
```

I have tried enabling the "Override software rendering list" option under chrome://flags but that did not help either.

I am running the 304.88 Xorg Driver for my older 8800GT which I got using the "Driver Manager" tool.

I have tried everything I could find on the web but no luck. Any thoughts? "Use hardware acceleration when available" is checked under advanced options but still no luck.

---

### Post by weatherman2 on 2015-08-25
I'm using kernel drivers for my Intel integrated video card, and here's what I get in Chrome:

```

Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Flash: Hardware accelerated
Flash Stage3D: Software only, hardware acceleration unavailable
Flash Stage3D Baseline profile: Software only, hardware acceleration unavailable
Compositing: Hardware accelerated
Multiple Raster Threads: Disabled
Rasterization: Software only, hardware acceleration unavailable
Threaded Rasterization: Enabled
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Hardware accelerated
WebGL: Hardware accelerated

```

Why does Chrome have hardware acceleration for some features and not others?  I don't know - I don't worry about it.  It has never been an issue for me.  Chrome works fine for me, but the laptop is slow anyway.

Do you see hardware acceleration unavilable for ALL features?

What kinds of issues are you having that you are trying to fix?

---

### Post by Yellow Pasque on 2015-08-26
> GPU access is disabled in chrome://settings

Try the simplest fix first. Go into chrome://settings, click on show advanced settings at the bottom, and then scroll down to the bottom again and make sure "use hardware acceleration when available" is checked.

---

### Post by chris408 on 2015-08-30
> **Temüjin said:**
> Try the simplest fix first. Go into chrome://settings, click on show advanced settings at the bottom, and then scroll down to the bottom again and make sure "use hardware acceleration when available" is checked.

I checked most of the simple stuff and yes this is selected. Any other thoughts?

---

### Post by chris408 on 2015-09-09
Anyone?

---

### Post by Yellow Pasque on 2015-09-09
Google has probably blacklisted your GPU because of some driver bug. Try this and see if it helps:
```
google-chrome --ignore-gpu-blacklist --enable-webgl
```

---

### Post by chris408 on 2015-09-16
> **Temüjin said:**
> Google has probably blacklisted your GPU because of some driver bug. Try this and see if it helps:
```
google-chrome --ignore-gpu-blacklist --enable-webgl
```

I tried this and then went into chrome:gpu and this is what I see. Looks pretty much the same

```
[COLOR=#000000][FONT=sans-serif][h=3]Graphics Feature Status[/h]
[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash Stage3D: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Compositing: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Multiple Raster Threads: [COLOR=#FF0000]Disabled[/COLOR]
[*]Rasterization: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Threaded Rasterization: [COLOR=#FF0000]Unavailable[/COLOR]
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Video Encode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]WebGL: [COLOR=#FF0000]Unavailable[/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Driver Bug Workarounds[/h]
[LIST]
[*]clear_uniforms_before_first_program_use
[*]init_gl_position_in_vertex_shader
[*]init_vertex_attributes
[*]scalarize_vec_and_mat_constructor_args
[*]use_current_program_after_successful_link
[*]use_virtualized_gl_contexts
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Problems Detected[/h]
[LIST]
[*]GPU process was unable to boot: GPU access is disabled in chrome://settings.
*Disabled Features: [COLOR=#FF0000]all[/COLOR]*
[*][I]Always call glUseProgram after a successful link to avoid a driver bug: [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]use_current_program_after_successful_link[/COLOR]*[/I]
[*][I][I]Program link fails in NVIDIA Linux if gl_Position is not set: [286468]("http://crbug.com/286468")
*Applied Workarounds: [COLOR=#808000]init_gl_position_in_vertex_shader[/COLOR]*[/I][/I]
[*][I][I][I]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*[/I][/I][/I]
[*][I][I][I]Linux NVIDIA drivers don't have the correct defaults for vertex attributes: [351528]("http://crbug.com/351528")
*Applied Workarounds: [COLOR=#808000]init_vertex_attributes[/COLOR]*[/I][/I][/I]
[*][I][I][I]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]*[/I][/I][/I]
[*][I][I][I]MakeCurrent is slow on Linux
*Applied Workarounds: [COLOR=#808000]use_virtualized_gl_contexts[/COLOR]*[/I][/I][/I]
[*][I][I][I]Raster is using a single thread.
*Disabled Features: [COLOR=#FF0000]multiple_raster_threads[/COLOR]*[/I][/I][/I]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Version Information*[/I][/I][/h][TABLE="width: 1238"]
[TR]
[TD]**Data exported**[/TD]
[TD]9/16/2015, 9:50:52 AM[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/44.0.2403.157[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 3.5.0-17-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list version**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Driver bug list version**[/TD]
[TD]8.19[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]709dc46cbd06[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia[/TD]
[/TR]
[TR]
[TD]**Command Line Args**[/TD]
[TD]--ignore-gpu-blacklist --enable-webglgoogle-chrome --ignore-gpu-blacklist --enable-webgl --flag-switches-begin --force-gpu-rasterization --ignore-gpu-blacklist --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Driver Information*[/I][/I][/h][TABLE="width: 1238"]
[TR]
[TD]**Initialization time**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x10de, DEVICE= 0x0611[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]NVIDIA[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]304.88[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]Marco[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x0000[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]1[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Log Messages*[/I][/I][/h]
[LIST]
[*]*[I][I]GpuProcessHostUIShim: The GPU process exited with code 32512.*[/I][/I]
[/LIST]
[/FONT][/COLOR]

```

---

### Post by Yellow Pasque on 2015-09-16
This is the best I could google:
[https://code.google.com/p/chromium/issues/detail?id=506950](https://code.google.com/p/chromium/issues/detail?id=506950)

```

GPU process crash count	1
GpuProcessHostUIShim: The GPU process exited with code 32512.

```

As the bug report suggests, submit the crash ID (enable crash reporting if not enabled already). [http://www.chromium.org/for-testers/bug-reporting-guidelines/reporting-crash-bug](http://www.chromium.org/for-testers/bug-reporting-guidelines/reporting-crash-bug)

---

