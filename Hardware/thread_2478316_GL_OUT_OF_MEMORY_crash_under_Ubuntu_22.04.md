---
title: "GL_OUT_OF_MEMORY crash under Ubuntu 22.04"
date: 2022-08-22
forum: Hardware
---

### Post by strophy on 2022-08-22
Hi, I have a brand new Lenovo Z16 with Ryzen 6850H and Radeon RX  6500M. I'm using Ubuntu 22.04 I've installed the `amdgpu` drivers  (version 22.20) and I can reliably cause a crash by resizing a window  for an Electron app like VS Code, Slack or Spotify. The Gnome log contains the  following information:

[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: Failed to allocate a buffer:[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: size : 5791744 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: alignment : 2097152 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: domains : 4[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: flags : 6[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: Failed to allocate a buffer:[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: size : 4612096 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: alignment : 2097152 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: domains : 4[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: flags : 6[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: Failed to allocate a buffer:[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: size : 4612096 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: alignment : 2097152 bytes[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: domains : 4[/FONT]
[FONT=courier new,courier]Aug 22 16:50:38 z16 code.desktop[58141]: amdgpu: flags : 6[/FONT]
[FONT=courier new,courier]Aug  22 16:50:38 z16 code.desktop[58141]:  [58141:0822/165038.636620:ERROR:angle_platform_impl.cc(44)]  renderergl_utils.cpp:2512 (CheckError): GL call  functions->texStorage2D(ToGLenum(type),  static_cast<GLsizei>(levels), texStorageFormat.internalFormat,  size.width, size.height) generated error 0x00000505 in  ../../third_party/angle/src/libANGLE/renderer/gl/TextureGL.cpp,  setStorage:1036.[/FONT]
[FONT=courier new,courier]Aug 22  16:50:38 z16 code.desktop[58141]:  [58141:0822/165038.636815:ERROR:shared_context_state.cc(826)]  SharedContextState lost due to GL_OUT_OF_MEMORY[/FONT]
[FONT=courier new,courier]Aug  22 16:50:38 z16 code.desktop[58141]:  [58141:0822/165038.637181:ERROR:gpu_service_impl.cc(977)] Exiting GPU  process because some drivers can't recover from errors. GPU process will  restart shortly.[/FONT]
[FONT=courier new,courier]Aug 22  16:50:39 z16 code.desktop[7662]:  [7662:0822/165039.696792:ERROR:gpu_process_host.cc(979)] GPU process  exited unexpectedly: exit_code=8704[/FONT]
[FONT=courier new,courier]Aug  22 16:50:39 z16 code.desktop[64206]: libva error:  vaGetDriverNameByIndex() failed with unknown libva error, driver_name =  (null)[/FONT]
[FONT=courier new,courier]Aug 22 16:50:39 z16  code.desktop[64206]:  [64206:0822/165039.751487:ERROR:sandbox_linux.cc(377)]  InitializeSandbox() called with multiple threads in process gpu-process.[/FONT]
[FONT=courier new,courier]Aug  22 16:50:43 z16 code.desktop[64206]:  [64206:0822/165043.064314:ERROR:gl_surface_presentation_helper.cc(260)]  GetVSyncParametersIfAvailable() failed for 1 times![/FONT]
[FONT=courier new,courier]Aug  22 16:50:44 z16 code.desktop[64206]:  [64206:0822/165044.106055:ERROR:gl_surface_presentation_helper.cc(260)]  GetVSyncParametersIfAvailable() failed for 2 times![/FONT]
[FONT=courier new,courier]Aug  22 16:50:44 z16 code.desktop[64206]:  [64206:0822/165044.111067:ERROR:gl_surface_presentation_helper.cc(260)]  GetVSyncParametersIfAvailable() failed for 3 times![/FONT]

The app then becomes unusable and needs to be restarted, and after a while a full system restart is necessary. How can I go about diagnosing this issue?

---

### Post by Yellow Pasque on 2022-08-23
Are you running the program(s) on the integrated GPU or the discrete GPU? If unsure, please post output of:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

---

### Post by strophy on 2022-08-23
Thanks for the quick reply. It looks like apps are using the iGPU by default:

[FONT=courier new]strophy@z16:~$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD YELLOW_CARP (LLVM 14.0.1, DRM 3.46, 5.15.0-46-generic) (0x1681)
    Version: 22.1.0
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 31 MB, largest block: 31 MB
    VBO free aux. memory - total: 30838 MB, largest block: 30838 MB
    Texture free memory - total: 31 MB, largest block: 31 MB
    Texture free aux. memory - total: 30838 MB, largest block: 30838 MB
    Renderbuffer free memory - total: 31 MB, largest block: 31 MB
    Renderbuffer free aux. memory - total: 30838 MB, largest block: 30838 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 31866 MB
    Currently available dedicated video memory: 31 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD YELLOW_CARP (LLVM 14.0.1, DRM 3.46, 5.15.0-46-generic)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 22.1.0-devel
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 22.1.0-devel
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

strophy@z16:~$ DRI_PRIME=1 glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD Radeon RX 6500 (beige_goby, LLVM 14.0.1, DRM 3.46, 5.15.0-46-generic) (0x743f)
    Version: 22.1.0
    Accelerated: yes
    Video memory: 4096MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 4069 MB, largest block: 4069 MB
    VBO free aux. memory - total: 31343 MB, largest block: 31343 MB
    Texture free memory - total: 4069 MB, largest block: 4069 MB
    Texture free aux. memory - total: 31343 MB, largest block: 31343 MB
    Renderbuffer free memory - total: 4069 MB, largest block: 4069 MB
    Renderbuffer free aux. memory - total: 31343 MB, largest block: 31343 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 4096 MB
    Total available memory: 35450 MB
    Currently available dedicated video memory: 4069 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD Radeon RX 6500 (beige_goby, LLVM 14.0.1, DRM 3.46, 5.15.0-46-generic)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 22.1.0-devel
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 22.1.0-devel
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20[/FONT]


This makes sense to me for power usage reasons. My old Lenovo W540 had an intel iGPU and NVIDIA dGPU, and for most apps using the iGPU was the right choice. To test if the iGPU was causing the problems, I tried running `[FONT=courier new]DRI_PRIME=1 code .[FONT=arial]` to[/FONT][/FONT] force VS Code to use the dGPU. This resolves the problem, but I believe the underlying bug probably still exists, it's just that the dGPU has enough memory that it doesn't need to swap anything with the system memory. I looked at my old W540 intel iGPU and found it shows:

[FONT=courier new]Video memory: 1536MB
Unified memory: yes[/FONT]

This differs to the lower amount of memory and no unified memory shown above for the AMD iGPU. Maybe this is the problem?

---

### Post by strophy on 2022-08-23
I tried adjusting the UMA Frame Buffer size in UEFI from "Auto" to 2GB, without any change to the above output. This is surprising since I expected this would affect the "Unified memory" output. While testing, I also noticed the following appears in dmesg each time the graphics thread crashes:

[FONT=courier new][ 1046.662006] [drm] PCIE GART of 512M enabled (table at 0x0000008000000000).
[ 1046.662031] [drm] PSP is resuming...
[ 1046.736906] [drm] reserve 0xa00000 from 0x80fe000000 for PSP TMR
[ 1046.829256] amdgpu 0000:03:00.0: amdgpu: RAS: optional ras ta ucode is not available
[ 1046.844243] amdgpu 0000:03:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
[ 1046.844247] amdgpu 0000:03:00.0: amdgpu: SMU is resuming...
[ 1046.844251] amdgpu 0000:03:00.0: amdgpu: smu driver if version = 0x0000000d, smu fw if version = 0x0000000f, smu fw program = 0, version = 0x00491c00 (73.28.0)
[ 1046.844256] amdgpu 0000:03:00.0: amdgpu: SMU driver if version not matched
[ 1046.881678] amdgpu 0000:03:00.0: amdgpu: SMU is resumed successfully!
[ 1046.883001] [drm] DMUB hardware initialized: version=0x02020013
[ 1046.896751] [drm] kiq ring mec 2 pipe 1 q 0
[ 1046.899989] [drm] VCN decode and encode initialized successfully(under DPG Mode).
[ 1046.900005] amdgpu 0000:03:00.0: amdgpu: ring gfx_0.0.0 uses VM inv eng 0 on hub 0
[ 1046.900007] amdgpu 0000:03:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[ 1046.900009] amdgpu 0000:03:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[ 1046.900010] amdgpu 0000:03:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[ 1046.900011] amdgpu 0000:03:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[ 1046.900012] amdgpu 0000:03:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[ 1046.900013] amdgpu 0000:03:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[ 1046.900013] amdgpu 0000:03:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[ 1046.900014] amdgpu 0000:03:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[ 1046.900015] amdgpu 0000:03:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[ 1046.900016] amdgpu 0000:03:00.0: amdgpu: ring sdma0 uses VM inv eng 12 on hub 0
[ 1046.900017] amdgpu 0000:03:00.0: amdgpu: ring vcn_dec_0 uses VM inv eng 0 on hub 1
[ 1053.228874] [drm] free PSP TMR buffer
[ 1060.139167] warn_alloc: 23 callbacks suppressed
[ 1060.139170] code: page allocation failure: order:0, mode:0x104dc4(GFP_USER|GFP_DMA32|__GFP_RETRY_MAYFAIL|__GFP_ZERO), nodemask=(null),cpuset=user.slice,mems_allowed=0
[ 1060.139178] CPU: 4 PID: 22559 Comm: code Tainted: G           O      5.15.0-46-generic #49-Ubuntu
[ 1060.139180] Hardware name: LENOVO 21D4000HUS/21D4000HUS, BIOS N3GET37W (1.18 ) 07/27/2022
[ 1060.139181] Call Trace:
[ 1060.139183]  <TASK>
[ 1060.139185]  show_stack+0x52/0x5c
[ 1060.139189]  dump_stack_lvl+0x4a/0x63
[ 1060.139193]  dump_stack+0x10/0x16
[ 1060.139194]  warn_alloc+0x138/0x160
[ 1060.139197]  __alloc_pages_slowpath.constprop.0+0xa0b/0xa40
[ 1060.139198]  __alloc_pages+0x311/0x330
[ 1060.139199]  alloc_pages+0x9e/0x1e0
[ 1060.139204]  amdttm_pool_alloc+0x38e/0x520 [amdttm]
[ 1060.139210]  amdgpu_ttm_tt_populate+0x3c/0x90 [amdgpu]
[ 1060.139339]  amdttm_tt_populate+0xb6/0x190 [amdttm]
[ 1060.139343]  ttm_bo_handle_move_mem+0x1d4/0x240 [amdttm]
[ 1060.139345]  amdttm_bo_validate+0xc3/0x110 [amdttm]
[ 1060.139347]  ? drm_vma_offset_add+0x5a/0x70 [drm]
[ 1060.139363]  amdttm_bo_init_reserved+0x1dd/0x270 [amdttm]
[ 1060.139366]  amdgpu_bo_create+0x1c1/0x620 [amdgpu]
[ 1060.139433]  ? amdgpu_bo_vm_destroy+0x80/0x80 [amdgpu]
[ 1060.139499]  ? mutex_lock+0x13/0x50
[ 1060.139504]  amdgpu_bo_create_user+0x38/0x70 [amdgpu]
[ 1060.139565]  amdgpu_gem_object_create+0xa7/0x150 [amdgpu]
[ 1060.139629]  ? amdgpu_bo_vm_destroy+0x80/0x80 [amdgpu]
[ 1060.139689]  amdgpu_gem_create_ioctl+0x121/0x320 [amdgpu]
[ 1060.139749]  ? sock_recvmsg+0x78/0x80
[ 1060.139753]  ? amdgpu_gem_force_release+0x170/0x170 [amdgpu]
[ 1060.139817]  drm_ioctl_kernel+0xb2/0x100 [drm]
[ 1060.139879]  drm_ioctl+0x268/0x4b0 [drm]
[ 1060.139887]  ? amdgpu_gem_force_release+0x170/0x170 [amdgpu]
[ 1060.139967]  ? ___sys_recvmsg+0x99/0x110
[ 1060.139972]  amdgpu_drm_ioctl+0x4e/0x90 [amdgpu]
[ 1060.140040]  __x64_sys_ioctl+0x95/0xd0
[ 1060.140044]  do_syscall_64+0x5c/0xc0
[ 1060.140046]  ? read_hpet+0x1c/0x40
[ 1060.140050]  ? ktime_get_real_ts64+0x55/0xf0
[ 1060.140053]  ? _copy_to_user+0x20/0x30
[ 1060.140056]  ? __x64_sys_gettimeofday+0xb0/0xd0
[ 1060.140059]  ? exit_to_user_mode_prepare+0x37/0xb0
[ 1060.140060]  ? syscall_exit_to_user_mode+0x27/0x50
[ 1060.140062]  ? do_syscall_64+0x69/0xc0
[ 1060.140063]  ? syscall_exit_to_user_mode+0x27/0x50
[ 1060.140064]  ? __x64_sys_recvmsg+0x1d/0x30
[ 1060.140068]  ? do_syscall_64+0x69/0xc0
[ 1060.140068]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
[ 1060.140071] RIP: 0033:0x7f0e1cf78aff
[ 1060.140073] Code: 00 48 89 44 24 18 31 c0 48 8d 44 24 60 c7 04 24 10 00 00 00 48 89 44 24 08 48 8d 44 24 20 48 89 44 24 10 b8 10 00 00 00 0f 05 <41> 89 c0 3d 00 f0 ff ff 77 1f 48 8b 44 24 18 64 48 2b 04 25 28 00
[ 1060.140075] RSP: 002b:00007ffec6c98cf0 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
[ 1060.140076] RAX: ffffffffffffffda RBX: 00007ffec6c98da0 RCX: 00007f0e1cf78aff
[ 1060.140077] RDX: 00007ffec6c98da0 RSI: 00000000c0206440 RDI: 0000000000000017
[ 1060.140078] RBP: 00000000c0206440 R08: 0000000000000000 R09: 0000000000000000
[ 1060.140079] R10: 000008b801dd6728 R11: 0000000000000246 R12: 0000000000200000
[ 1060.140079] R13: 0000000000000017 R14: 0000000000456000 R15: 000008b8006d1700
[ 1060.140080]  </TASK>
[ 1060.140081] Mem-Info:
[ 1060.140083] active_anon:2999 inactive_anon:841798 isolated_anon:0
                active_file:148069 inactive_file:158813 isolated_file:0
                unevictable:4 dirty:3236 writeback:0
                slab_reclaimable:18396 slab_unreclaimable:46243
                mapped:231000 shmem:63534 pagetables:11097 bounce:0
                kernel_misc_reclaimable:0
                free:6276584 free_pcp:238 free_cma:0
[ 1060.140086] Node 0 active_anon:11996kB inactive_anon:3367192kB active_file:592276kB inactive_file:635252kB unevictable:16kB isolated(anon):0kB isolated(file):0kB mapped:924000kB dirty:12944kB writeback:0kB shmem:254136kB shmem_thp: 0kB shmem_pmdmapped: 0kB anon_thp: 0kB writeback_tmp:0kB kernel_stack:25856kB pagetables:44388kB all_unreclaimable? no
[ 1060.140088] Node 0 DMA free:6696kB min:32kB low:44kB high:56kB reserved_highatomic:0KB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:15996kB managed:15360kB mlocked:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
[ 1060.140091] lowmem_reserve[]: 0 1667 31245 31245 31245
[ 1060.140093] Node 0 DMA32 free:16040kB min:3604kB low:5308kB high:7012kB reserved_highatomic:0KB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:1863180kB managed:1795204kB mlocked:0kB bounce:0kB free_pcp:496kB local_pcp:240kB free_cma:0kB
[ 1060.140095] lowmem_reserve[]: 0 0 29578 29578 29578
[ 1060.140096] Node 0 Normal free:25083600kB min:63944kB low:94232kB high:124520kB reserved_highatomic:0KB active_anon:11996kB inactive_anon:3367108kB active_file:592472kB inactive_file:635756kB unevictable:16kB writepending:12944kB present:30903296kB managed:30296896kB mlocked:16kB bounce:0kB free_pcp:456kB local_pcp:0kB free_cma:0kB
[ 1060.140099] lowmem_reserve[]: 0 0 0 0 0
[ 1060.140100] Node 0 DMA: 0*4kB 1*8kB (U) 0*16kB 1*32kB (U) 0*64kB 0*128kB 0*256kB 1*512kB (U) 0*1024kB 1*2048kB (M) 1*4096kB (M) = 6696kB
[ 1060.140106] Node 0 DMA32: 30*4kB (U) 15*8kB (U) 45*16kB (U) 50*32kB (U) 23*64kB (U) 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 3*4096kB (U) = 16320kB
[ 1060.140111] Node 0 Normal: 35978*4kB (UME) 12961*8kB (UME) 4530*16kB (UME) 2380*32kB (UME) 2019*64kB (UME) 335*128kB (UME) 798*256kB (UME) 295*512kB (UME) 99*1024kB (ME) 38*2048kB (UME) 5855*4096kB (M) = 25084944kB
[ 1060.140117] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
[ 1060.140118] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[ 1060.140119] 370325 total pagecache pages
[ 1060.140120] 0 pages in swap cache
[ 1060.140121] Swap cache stats: add 0, delete 0, find 0/0
[ 1060.140122] Free swap  = 2097148kB
[ 1060.140122] Total swap = 2097148kB
[ 1060.140123] 8195618 pages RAM
[ 1060.140123] 0 pages HighMem/MovableOnly
[ 1060.140123] 168753 pages reserved
[ 1060.140123] 0 pages hwpoisoned

[/FONT]

---

### Post by Yellow Pasque on 2022-08-23
Hmm. A shot in the dark says you may want to try booting with 'amdgpu.no_system_mem_limit=1'. If you need help with that, just ask.
> **no_system_mem_limit(bool)**
Disable system memory limit, to support multiple process shared memory
Reference: [https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html](https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html)

---

### Post by strophy on 2022-08-23
Thanks, I added this boot parameter temporarily by pressing 'e' during GRUB and adding the parameter to the line starting with 'linux'. The problem remains after booting like this, and Unified memory still reads 'no' in the glxinfo output. My only workaround for this at the moment is to add DRI_PRIME=1 to /etc/environment to force use of the dGPU by all apps. The underlying bug is still present of course, but I'm not sure if it is in the BIOS/UEFI for this particular machine, or in the drm/amdgpu driver?

---

### Post by Yellow Pasque on 2022-08-28
>  The underlying bug is still present of course, but I'm not sure if it is in the BIOS/UEFI for this particular machine, or in the drm/amdgpu driver? 
Do you still have Windows on this system or did you obliterate it?

---

### Post by strophy on 2022-08-28
I still have Windows 11 on another partition, you think the same test resizing an Electron app will be worth testing there?

---

### Post by Yellow Pasque on 2022-08-29
> **strophy said:**
> I still have Windows 11 on another partition, you think the same test resizing an Electron app will be worth testing there?

No, I was thinking of looking at the video memory to see whether changing the UMA value in the BIOS had any effect on reported video memory.

---

### Post by strophy on 2022-08-29
Good idea. I tried with UMA set to Auto, 1G and 2G and took screenshots of both the 680M iGPU and 6500M dGPU in GPU-Z. There is no difference in reported memory, I also checked under the various sections of the Advanced tab and couldn't observe any change in reported memory. But I also think this hardware is still too new to be identified correctly, e.g. it is showing a lot of blank spaces for the 680M device and a generic "AMD Radeon Graphics" instead of the precise model number - same behavior as needing to update from 21 to 22 drivers in order to see the proper device name of the 6500M. I think we are barking up the wrong tree here anyway though, because a Z13 user over on the Lenovo forums (same iGPU) posted his glxinfo output here and the Unified memory is also marked "no" there, so either these devices are being detected incorrectly or this configuration is irrelevant or intel-only maybe. I've attached my GPU-Z screenshots here anyway.

I tried updating the Ubuntu kernel using mainline and I'm now running 5.19.3, the bug still persists. I also tried running Manjaro Linux, and did not observe the bug. How can I try to narrow this down better? e.g. I'm also noticing a lag from when first moving the USB mouse on this device to when it actually starts picking up movement.

---

### Post by Yellow Pasque on 2022-08-29
My Ryzen 5600G APU also says "unified memory:no", so I'm a bit skeptical on that diagnostic.
However, when I change the UMA size in the EFI, I can see the memory change accordingly. so with 2G:
```
  Device: RENOIR (renoir, LLVM 14.0.6, DRM 3.47, 5.19.4-1-siduction-amd64) (0x1638)
    Version: 22.2.0
    Accelerated: yes
    Video memory: 2048MB
    Unified memory: no
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 1358 MB, largest block: 1358 MB
    VBO free aux. memory - total: 6842 MB, largest block: 6842 MB
    Texture free memory - total: 1358 MB, largest block: 1358 MB
    Texture free aux. memory - total: 6842 MB, largest block: 6842 MB
    Renderbuffer free memory - total: 1358 MB, largest block: 1358 MB
    Renderbuffer free aux. memory - total: 6842 MB, largest block: 6842 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 2048 MB
    Total available memory: 8977 MB
    Currently available dedicated video memory: 1358 MB
```

So if the UMA size isn't having an effect, I feel like that part's a BIOS/EFI bug. Or maybe it's a quirk of hybrid graphics.

Anyway, after some Googling, I see that GL_OUT_OF_MEMORY may not mean you're literally out of (video) memory. It could be a driver failure. That seems more likely if you can't reproduce the problem on Manjaro.

---

### Post by Yellow Pasque on 2022-08-29
Sorry to double post, but I had more thoughts. You may want to try oibaf's PPA to see if having all the latest upstream components helps. And you may want to see if you can reproduce with Xserver vs. running Wayland. After that, I think it's AMD bug report time.

EDIT (forgot link): [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=jammy](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=jammy)

---

### Post by strophy on 2022-09-01
Hi, thanks for all the ideas! I tried running `glxinfo -B` with both GPUs (using DRI_PRIME=0/1), before and after setting UMA Frame buffer Size to 2GB, 8GB and Auto. The output does not differ at all, but I agree this is unlikely to be the cause of the error. Weird to find a BIOS setting that apparently has no effect.

I then installed the oibaf PPA and ran `sudo apt update && sudo apt upgrade`, which installed a ton of stuff. I also used mainline to update my kernel to 5.19.5. `glxinfo -B` still shows `Version: 22.1.0` so I'm unsure if this actually changed anything. Your version above shows `22.2.0` so I wonder where this driver comes from? I'm really unclear if I need to update the kernel or update PPAs in order to update drivers under Linux, but either way, after updating both to oibaf's PPA and updating the kernel, the issue is still reproducible.

Finally, I tried logging in with X11 instead of Wayland. I am able to cause all manner of visual artifacts, flickering and tearing by simply resizing the VS Code window, and in a few seconds I can crash the graphics thread causing the window to go black. However, it still manages to recover and the window is usable afterwards, whereas on Wayland the crash requires closing the app (and sometimes even the session).

While testing all this, I had one weird crash under Wayland while not doing anything where the screen went dark, came back and no interaction was possible. I tried switching to another console to view `dmesg` output but although the Ctrl + Alt + F<n> cleared the screen and sometimes showed some text output, I was unable to login on a different session. Upon pressing Ctrl + Alt + F2 to go back to the main Wayland session both monitors were completely garbled (see photo) and a hard power off was necessary. I'm also having sporadic issues waking up from sleep. I agree it's time to file a bug report with AMD (and maybe Lenovo about the BIOS?). Is this the right location? [https://gitlab.freedesktop.org/drm/amd/-/issues](https://gitlab.freedesktop.org/drm/amd/-/issues)

---

### Post by Yellow Pasque on 2022-09-03
> **strophy said:**
> I agree it's time to file a bug report with AMD (and maybe Lenovo about the BIOS?). Is this the right location? [https://gitlab.freedesktop.org/drm/amd/-/issues](https://gitlab.freedesktop.org/drm/amd/-/issues)

Yeah, that's right. I've been googling this for a couple days and I'm out of ideas. :\

---

### Post by strophy on 2022-09-04
Thanks for your help! amdgpu issue opened here: [https://gitlab.freedesktop.org/drm/amd/-/issues/2149](https://gitlab.freedesktop.org/drm/amd/-/issues/2149)

---

