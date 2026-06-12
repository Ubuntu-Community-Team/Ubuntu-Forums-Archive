---
title: "dkms stuck while building nvidia module"
date: 2016-05-13
forum: Hardware
---

### Post by 9600xt on 2016-05-13
Hi, I was trying to install Nvidia 364.19 driver from [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) on Ubuntu 16.04 on my laptop msi-ge60 2pe with a gtx 860m, but installation will stuck at:
```
Loading new nvidia-364-364.19 DKMS files...First Installation: checking all kernels...
Building only for 4.6.0-040600rc7-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc7-generic

```
[the same with all other kenel on my system (4.4.0 and 4.2.0 too)], now i must interrupt the installation with CTRL-C and i need to do:
```

sudo apt-get purge *nvidia

```
to restore apt-get functionality, otherwise every time i try to install or remove some package i receive the "misconfigured packages, you need to run *sudo dpkg --configure -a* command to complete configuration", but if i do that i will return at:
 ```
Loading new nvidia-364-364.19 DKMS files...First Installation: checking all kernels...
Building only for 4.6.0-040600rc7-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc7-generic

```

So... some time ago i was able to install nvidia driver on this PC from this repo, but at least by 2 months until now I cannot do it anymore, what's changed??? Maybe updating to Ubuntu 16.04 is the cause!?? The thing that I can not understand is why I do not receive any kind of error from DKMS module bilder, if some module fails to build i shuld receive an error not to remain stuck. With other software modules DKMS works correctly eg. VirtualBox modules or VMWare modules....

Please help me to understant what is the problem, I don't know where to look for, because no error are showing....

---

### Post by Yellow Pasque on 2016-05-13
Does 364.19 support 4.6.x kernels?
The make log might offer more clues:
/var/lib/dkms/nvidia/364.19/`uname -r`/x86_64/log/make.log

---

### Post by 9600xt on 2016-05-13
From official ppa changelog:
```
**Changelog**

nvidia-graphics-drivers-364 (364.19-0ubuntu0~gpu16.04.2) xenial; urgency=medium

  *  debian/templates/dkms_nvidia.conf.in,
     debian/dkms_nvidia/patches/buildfix_kernel_4.6.patch:
     - Add support for Linux 4.6.
 [COLOR=#333333] -- Rico Tzschichholz <ricotz@ubuntu.com>  Sun, 08 May 2016 18:11:42 +0200[/COLOR]
```
so I think kernel 4.6 should be supported... anyway I have this problem when i try to build over kernel 4.4.0 and 4.2.0 too....

This is what I did rirght now:
```
andrea@laptop-andrea:~$ sudo apt-get install --reinstall nvidia-364 bumblebee primus libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 mesa-utils xserver-xorg-video-intel
[sudo] password di andrea: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
The following additional packages will be installed:
  nvidia-settings
I seguenti pacchetti NUOVI saranno installati:
  nvidia-364 nvidia-settings
0 aggiornati, 2 installati, 8 reinstallati, 0 da rimuovere e 24 non aggiornati.
È necessario scaricare 69,4 MB/81,7 MB di archivi.
Dopo quest'operazione, verranno occupati 307 MB di spazio su disco.
Continuare? [S/n] S
Scaricamento di:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 nvidia-364 amd64 364.19-0ubuntu0~gpu16.04.2 [68,6 MB]
Scaricamento di:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 nvidia-settings amd64 364.15-0ubuntu0~gpu16.04.2 [865 kB]
Recuperati 69,4 MB in 4min 28s (259 kB/s)                                      
(Lettura del database... 411634 file e directory attualmente installati.)
Preparativi per estrarre .../bumblebee_3.2.1-10_amd64.deb...
Estrazione di bumblebee (3.2.1-10) su (3.2.1-10)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605130730.8f05a0~gd~x_amd64.deb...
Estrazione di libgl1-mesa-dri:amd64 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605130730.8f05a0~gd~x_i386.deb...
Estrazione di libgl1-mesa-dri:i386 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605130730.8f05a0~gd~x_amd64.deb...
Estrazione di libgl1-mesa-glx:amd64 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605130730.8f05a0~gd~x_i386.deb...
Estrazione di libgl1-mesa-glx:i386 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Selezionato il pacchetto nvidia-364 non precedentemente selezionato.
Preparativi per estrarre .../nvidia-364_364.19-0ubuntu0~gpu16.04.2_amd64.deb...
Estrazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.2)...
Selezionato il pacchetto nvidia-settings non precedentemente selezionato.
Preparativi per estrarre .../nvidia-settings_364.15-0ubuntu0~gpu16.04.2_amd64.deb...
Estrazione di nvidia-settings (364.15-0ubuntu0~gpu16.04.2)...
Preparativi per estrarre .../xserver-xorg-video-intel_2%3a2.99.917+git1605091646.88733a~gd~x_amd64.deb...
Estrazione di xserver-xorg-video-intel (2:2.99.917+git1605091646.88733a~gd~x) su (2:2.99.917+git1605091646.88733a~gd~x)...
Preparativi per estrarre .../mesa-utils_8.3.0-1_amd64.deb...
Estrazione di mesa-utils (8.3.0-1) su (8.3.0-1)...
Preparativi per estrarre .../primus_0~20150328-1_amd64.deb...
Estrazione di primus (0~20150328-1) su (0~20150328-1)...
Elaborazione dei trigger per initramfs-tools (0.122ubuntu8)...
update-initramfs: Generating /boot/initrd.img-4.6.0-040600rc7-generic
cp: impossibile eseguire stat di '/etc/modprobe.d/nvidia-graphics-drivers.conf': File o directory non esistente
E: /usr/share/initramfs-tools/hooks/copy-nvidia-options failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.6.0-040600rc7-generic with 1.
dpkg: errore nell'elaborare il pacchetto initramfs-tools (--unpack):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
Elaborazione dei trigger per man-db (2.7.5-1)...
Elaborazione dei trigger per systemd (229-4ubuntu4)...
Elaborazione dei trigger per ureadahead (0.100.0-19)...
Elaborazione dei trigger per libc-bin (2.23-0ubuntu3)...
Elaborazione dei trigger per bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1)...
Rebuilding /usr/share/applications/bamf-2.index...
Elaborazione dei trigger per desktop-file-utils (0.22-1ubuntu5)...
Elaborazione dei trigger per mime-support (3.59ubuntu1)...
Elaborazione dei trigger per gnome-menus (3.13.3-6ubuntu3)...
Si sono verificati degli errori nell'elaborazione:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then i did:
```
andrea@laptop-andrea:~$ sudo dpkg --configure -aConfigurazione di xserver-xorg-video-intel (2:2.99.917+git1605091646.88733a~gd~x)...
Configurazione di libgl1-mesa-dri:amd64 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di libgl1-mesa-dri:i386 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di initramfs-tools (0.122ubuntu8)...
update-initramfs: deferring update (trigger activated)
Configurazione di nvidia-settings (364.15-0ubuntu0~gpu16.04.2)...
Configurazione di libgl1-mesa-glx:amd64 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di libgl1-mesa-glx:i386 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di bumblebee (3.2.1-10)...
Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
edit the BusID line in /etc/bumblebee/xorg.conf.nouveau .
insserv: warning: script 'douane' missing LSB tags and overrides
Configurazione di mesa-utils (8.3.0-1)...
Configurazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.2)...
update-alternatives: viene usato /usr/lib/nvidia-364/ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/share/nvidia-364/glamor.conf per fornire /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in modalità automatica
INFO:Enable nvidia-364
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Aggiunta dell'utente di sistema «nvidia-persistenced» (UID 117) ...
Aggiunta del nuovo gruppo «nvidia-persistenced» (GID 128) ...
Aggiunta del nuovo utente «nvidia-persistenced» (UID 117) con gruppo «nvidia-persistenced» ...
La directory home «/» non è stata creata.
Loading new nvidia-364-364.19 DKMS files...
First Installation: checking all kernels...
Building only for 4.6.0-040600rc7-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc7-generic
```
and it will stuck there....

this is the log:
```
andrea@laptop-andrea:~$ /var/lib/dkms/nvidia/364.19/`uname -r`/x86_64/log/make.log
bash: /var/lib/dkms/nvidia/364.19/4.6.0-040600rc7-generic/x86_64/log/make.log: File o directory non esistente

```
as you can see this file doesn't exists....

but i have this one:
```
andrea@laptop-andrea:~$ cat /var/lib/dkms/nvidia-364/364.19/build/make.log
DKMS make.log for nvidia-364-364.19 for kernel 4.6.0-040600rc7-generic (x86_64)
ven 13 mag 2016, 12.47.47, CEST
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.6.0-040600rc7-generic/build M=/var/lib/dkms/nvidia-364/364.19/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: ingresso nella directory "/usr/src/linux-headers-4.6.0-040600rc7-generic"
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia-modeset/nv-modeset-kernel.o
 CONFTEST: INIT_WORK
 CONFTEST: remap_pfn_range
 CONFTEST: set_memory_uc
 CONFTEST: set_memory_array_uc
 CONFTEST: follow_pfn
 CONFTEST: set_pages_uc
 CONFTEST: vmap
 CONFTEST: change_page_attr
 CONFTEST: pci_get_class
 CONFTEST: pci_choose_state
 CONFTEST: vm_insert_page
andrea@laptop-andrea:~$
```

---

### Post by Yellow Pasque on 2016-05-13
Try this:
```
sudo cat /var/lib/dkms/nvidia/364.19/`uname -r`/x86_64/log/make.log
```

If not, then try looking in /var/lib/dkms/nvidia to see if you can find any sort of log.

---

### Post by 9600xt on 2016-05-13
```
andrea@laptop-andrea:~$ cat /var/lib/dkms/nvidia-364/364.19/build/make.log
DKMS make.log for nvidia-364-364.19 for kernel 4.6.0-040600rc7-generic (x86_64)
ven 13 mag 2016, 12.47.47, CEST
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.6.0-040600rc7-generic/build M=/var/lib/dkms/nvidia-364/364.19/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: ingresso nella directory "/usr/src/linux-headers-4.6.0-040600rc7-generic"
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia-modeset/nv-modeset-kernel.o
 CONFTEST: INIT_WORK
 CONFTEST: remap_pfn_range
 CONFTEST: set_memory_uc
 CONFTEST: set_memory_array_uc
 CONFTEST: follow_pfn
 CONFTEST: set_pages_uc
 CONFTEST: vmap
 CONFTEST: change_page_attr
 CONFTEST: pci_get_class
 CONFTEST: pci_choose_state
 CONFTEST: vm_insert_page
andrea@laptop-andrea:~$
```

---

### Post by Yellow Pasque on 2016-05-13
Interesting. Here's mine for comparison:
```
DKMS make.log for nvidia-364.19 for kernel 4.5.3-towo.1-siduction-amd64 (x86_64)
Thu May  5 14:17:19 EDT 2016
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.5.3-towo.1-siduction-amd64/build M=/var/lib/dkms/nvidia/364.19/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.5.3-towo.1-siduction-amd64/build NV_KERNEL_OUTPUT=/lib/modules/4.5.3-towo.1-siduction-amd64/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: Entering directory '/usr/src/linux-headers-4.5.3-towo.1-siduction-amd64'
  SYMLINK /var/lib/dkms/nvidia/364.19/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia/364.19/build/nvidia-modeset/nv-modeset-kernel.o
 CONFTEST: remap_pfn_range
 CONFTEST: follow_pfn
 CONFTEST: INIT_WORK
 CONFTEST: vmap
 CONFTEST: set_pages_uc
 CONFTEST: set_memory_uc
 CONFTEST: set_memory_array_uc
 CONFTEST: change_page_attr
 CONFTEST: pci_get_class
 CONFTEST: pci_choose_state
 CONFTEST: vm_insert_page
 CONFTEST: acpi_device_id
 CONFTEST: acquire_console_sem
 CONFTEST: console_lock
 CONFTEST: kmem_cache_create
 CONFTEST: on_each_cpu
 CONFTEST: smp_call_function
 CONFTEST: acpi_evaluate_integer
 CONFTEST: ioremap_cache
 CONFTEST: ioremap_wc
 CONFTEST: acpi_walk_namespace
 CONFTEST: pci_domain_nr
 CONFTEST: pci_dma_mapping_error
 CONFTEST: sg_alloc_table
 CONFTEST: sg_init_table
 CONFTEST: pci_get_domain_bus_and_slot
 CONFTEST: get_num_physpages
 CONFTEST: efi_enabled
 CONFTEST: proc_create_data
 CONFTEST: pde_data
 CONFTEST: proc_remove
 CONFTEST: pm_vt_switch_required
 CONFTEST: drm_driver_has_set_busid
 CONFTEST: xen_ioemu_inject_msi
 CONFTEST: phys_to_dma
 CONFTEST: get_dma_ops
 CONFTEST: write_cr4
 CONFTEST: for_each_online_node
 CONFTEST: of_parse_phandle
 CONFTEST: node_end_pfn
 CONFTEST: pci_bus_address
 CONFTEST: remap_page_range
 CONFTEST: address_space_init_once
 CONFTEST: kbasename
 CONFTEST: fatal_signal_pending
 CONFTEST: list_cut_position
 CONFTEST: hlist_for_each_entry
 CONFTEST: vzalloc
 CONFTEST: wait_on_bit_lock_argument_count
 CONFTEST: bitmap_clear
 CONFTEST: drm_dev_unref
 CONFTEST: drm_reinit_primary_mode_group
 CONFTEST: drm_atomic_set_mode_for_crtc
 CONFTEST: drm_atomic_clean_old_fb
 CONFTEST: i2c_adapter
 CONFTEST: pm_message_t
 CONFTEST: irq_handler_t
 CONFTEST: acpi_device_ops
 CONFTEST: acpi_op_remove
 CONFTEST: outer_flush_all
 CONFTEST: proc_dir_entry
 CONFTEST: scatterlist
 CONFTEST: sg_table
 CONFTEST: file_operations
 CONFTEST: vm_operations_struct
 CONFTEST: atomic_long_type
 CONFTEST: pci_save_state
 CONFTEST: file_inode
 CONFTEST: task_struct
 CONFTEST: kuid_t
 CONFTEST: dma_ops
 CONFTEST: dma_map_ops
 CONFTEST: noncoherent_swiotlb_dma_ops
 CONFTEST: fault_flags
 CONFTEST: atomic64_type
 CONFTEST: address_space
 CONFTEST: backing_dev_info
 CONFTEST: kernel_write
 CONFTEST: strnstr
 CONFTEST: iterate_dir
 CONFTEST: kstrtoull
 CONFTEST: get_user_pages_remote
 CONFTEST: drm_bus_present
 CONFTEST: drm_bus_has_bus_type
 CONFTEST: drm_bus_has_get_name
 CONFTEST: drm_bus_has_get_irq
 CONFTEST: drm_driver_has_legacy_dev_list
 CONFTEST: drm_crtc_state_has_connectors_changed
 CONFTEST: drm_init_functions_have_name_arg
 CONFTEST: drm_mode_connector_list_update_has_merge_type_bits_arg
 CONFTEST: dom0_kernel_present
 CONFTEST: drm_available
 CONFTEST: nvidia_grid_build
 CONFTEST: drm_atomic_available
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-frontend.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-instance.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-acpi.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-chrdev.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-cray.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-dma.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-gvi.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-i2c.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-mempool.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-mmap.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-p2p.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-pat.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-procfs.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-usermap.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-vm.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-vtophys.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/os-interface.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/os-mlock.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/os-pci.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/os-registry.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/os-usermap.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-modeset-interface.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv-pci-table.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nv_uvm_interface.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nvlink_linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/nvlink_pci.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/ebridge_linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia/ibmnpu_linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_utils.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_common.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_page_migration.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_page_migration_kepler.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_page_migration_maxwell.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_page_migration_pascal.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_channel_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/nvstatus.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_perf.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_common_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_channel_directed_tests.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_channel_basic_sanity_tests.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_kernel_events.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_kernel_counters.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_debug_session.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_gpu_ops_tests.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_lite.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_page_cache.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_lite_api.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_lite_prefetch.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_lite_region_tracking.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_mmu_mgmt_pascal.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_mmu_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_api.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_device_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_fault_buffer.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_fault_buffer_pascal.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_ctx_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_hashmap.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_pa_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_unit_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_va_trie.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_pagetbl_mgmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/mmu_fmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/gmmu_fmt.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_fault_handler.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_identity_map.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm_full_perf.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_tools.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_global.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_gpu.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_procfs.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_va_space.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_gpu_semaphore.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_mem.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_rm_mem.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_channel.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_lock.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_hal.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_range_tree.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_range_allocator.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_va_range.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_range_group.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_va_block.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_gpu_page_fault.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_events.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_module.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_mmu.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pte_batch.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_tlb_batch.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_push.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pushbuffer.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_thread_context.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_tracker.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kepler.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kepler_ce.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kepler_host.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kepler_mmu.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_maxwell.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_maxwell_host.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pascal.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pascal_ce.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pascal_host.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pascal_mmu.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pascal_fault_buffer.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_policy.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_utils.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kvmalloc.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pmm_gpu.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_migrate.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_map_external.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_user_channel.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_test_rng.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_range_tree_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_range_allocator_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_gpu_semaphore_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_mem_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_rm_mem_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_page_tree_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_tracker_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_push_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_channel_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_ce_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_lock_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_utils_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_kvmalloc_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_pmm_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_events_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_perf_module_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_get_rm_ptes_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_fault_buffer_flush_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm/uvm8_mmu_test.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-modeset/nvidia-modeset-linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-drv.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-utils.o
/var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-drv.c:67:18: warning: initialization from incompatible pointer type [-Wincompatible-pointer-types]
     .fb_create = nvidia_drm_framebuffer_create,
                  ^
/var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-drv.c:67:18: note: (near initialization for &#8216;nv_mode_config_funcs.fb_create&#8217;)
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-crtc.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-encoder.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-connector.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-gem.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-fb.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-modeset.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-mmap.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nvidia-drm-linux.o
  CC [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm/nv-pci-table.o
ld -r -o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-interface.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-frontend.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-instance.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-acpi.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-chrdev.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-cray.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-dma.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-gvi.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-i2c.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-mempool.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-mmap.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-p2p.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-pat.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-procfs.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-usermap.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-vm.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-vtophys.o /var/lib/dkms/nvidia/364.19/build/nvidia/os-interface.o /var/lib/dkms/nvidia/364.19/build/nvidia/os-mlock.o /var/lib/dkms/nvidia/364.19/build/nvidia/os-pci.o /var/lib/dkms/nvidia/364.19/build/nvidia/os-registry.o /var/lib/dkms/nvidia/364.19/build/nvidia/os-usermap.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-modeset-interface.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv-pci-table.o /var/lib/dkms/nvidia/364.19/build/nvidia/nv_uvm_interface.o /var/lib/dkms/nvidia/364.19/build/nvidia/nvlink_linux.o /var/lib/dkms/nvidia/364.19/build/nvidia/nvlink_pci.o /var/lib/dkms/nvidia/364.19/build/nvidia/ebridge_linux.o /var/lib/dkms/nvidia/364.19/build/nvidia/ibmnpu_linux.o
ld -r -o /var/lib/dkms/nvidia/364.19/build/nvidia-modeset/nv-modeset-interface.o /var/lib/dkms/nvidia/364.19/build/nvidia-modeset/nvidia-modeset-linux.o
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia.o
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm.o
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-modeset.o
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm.o
  Building modules, stage 2.
  MODPOST 4 modules
  CC      /var/lib/dkms/nvidia/364.19/build/nvidia-drm.mod.o
  CC      /var/lib/dkms/nvidia/364.19/build/nvidia-modeset.mod.o
  CC      /var/lib/dkms/nvidia/364.19/build/nvidia-uvm.mod.o
  CC      /var/lib/dkms/nvidia/364.19/build/nvidia.mod.o
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-drm.ko
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-uvm.ko
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia.ko
  LD [M]  /var/lib/dkms/nvidia/364.19/build/nvidia-modeset.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.5.3-towo.1-siduction-amd64'
```

---

### Post by 9600xt on 2016-05-13
Hehe... your looks like mine when it was working ;)

So? Anyone else?

---

### Post by ricotz on 2016-05-13
Try the packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/) if you picked up an earlier build.

---

### Post by 9600xt on 2016-05-13
> **ricotz said:**
> Try the packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/) if you picked up an earlier build.

```
andrea@laptop-andrea:~$ sudo apt-get install --reinstall nvidia-364 bumblebee primus libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 mesa-utils xserver-xorg-video-intelLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti NUOVI saranno installati:
  nvidia-364
0 aggiornati, 1 installati, 8 reinstallati, 0 da rimuovere e 24 non aggiornati.
È necessario scaricare 0 B/80,8 MB di archivi.
Dopo quest'operazione, verranno occupati 303 MB di spazio su disco.
(Lettura del database... 411620 file e directory attualmente installati.)
Preparativi per estrarre .../bumblebee_3.2.1-10_amd64.deb...
Estrazione di bumblebee (3.2.1-10) su (3.2.1-10)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605130730.8f05a0~gd~x_amd64.deb...
Estrazione di libgl1-mesa-dri:amd64 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605130730.8f05a0~gd~x_i386.deb...
Estrazione di libgl1-mesa-dri:i386 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605130730.8f05a0~gd~x_amd64.deb...
Estrazione di libgl1-mesa-glx:amd64 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605130730.8f05a0~gd~x_i386.deb...
Estrazione di libgl1-mesa-glx:i386 (11.3~git1605130730.8f05a0~gd~x) su (11.3~git1605130730.8f05a0~gd~x)...
Selezionato il pacchetto nvidia-364 non precedentemente selezionato.
Preparativi per estrarre .../nvidia-364_364.19-0ubuntu0~gpu16.04.2_amd64.deb...
Estrazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.2)...
Preparativi per estrarre .../xserver-xorg-video-intel_2%3a2.99.917+git1605091646.88733a~gd~x_amd64.deb...
Estrazione di xserver-xorg-video-intel (2:2.99.917+git1605091646.88733a~gd~x) su (2:2.99.917+git1605091646.88733a~gd~x)...
Preparativi per estrarre .../mesa-utils_8.3.0-1_amd64.deb...
Estrazione di mesa-utils (8.3.0-1) su (8.3.0-1)...
Preparativi per estrarre .../primus_0~20150328-1_amd64.deb...
Estrazione di primus (0~20150328-1) su (0~20150328-1)...
Elaborazione dei trigger per initramfs-tools (0.122ubuntu8)...
update-initramfs: Generating /boot/initrd.img-4.6.0-040600rc7-generic
cp: impossibile eseguire stat di '/etc/modprobe.d/nvidia-graphics-drivers.conf': File o directory non esistente
E: /usr/share/initramfs-tools/hooks/copy-nvidia-options failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.6.0-040600rc7-generic with 1.
dpkg: errore nell'elaborare il pacchetto initramfs-tools (--unpack):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
Elaborazione dei trigger per man-db (2.7.5-1)...
Elaborazione dei trigger per systemd (229-4ubuntu4)...
Elaborazione dei trigger per ureadahead (0.100.0-19)...
ureadahead will be reprofiled on next reboot
Elaborazione dei trigger per libc-bin (2.23-0ubuntu3)...
Si sono verificati degli errori nell'elaborazione:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrea@laptop-andrea:~$
```

```
andrea@laptop-andrea:~$ sudo dpkg --configure -aConfigurazione di xserver-xorg-video-intel (2:2.99.917+git1605091646.88733a~gd~x)...
Configurazione di libgl1-mesa-dri:amd64 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di libgl1-mesa-dri:i386 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di initramfs-tools (0.122ubuntu8)...
update-initramfs: deferring update (trigger activated)
Configurazione di libgl1-mesa-glx:amd64 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di libgl1-mesa-glx:i386 (11.3~git1605130730.8f05a0~gd~x)...
Configurazione di bumblebee (3.2.1-10)...
Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
edit the BusID line in /etc/bumblebee/xorg.conf.nouveau .
insserv: warning: script 'douane' missing LSB tags and overrides
Configurazione di mesa-utils (8.3.0-1)...
Configurazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.2)...
update-alternatives: viene usato /usr/lib/nvidia-364/ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/share/nvidia-364/glamor.conf per fornire /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in modalità automatica
INFO:Enable nvidia-364
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Aggiunta dell'utente di sistema «nvidia-persistenced» (UID 117) ...
Aggiunta del nuovo gruppo «nvidia-persistenced» (GID 128) ...
Aggiunta del nuovo utente «nvidia-persistenced» (UID 117) con gruppo «nvidia-persistenced» ...
La directory home «/» non è stata creata.
Loading new nvidia-364-364.19 DKMS files...
First Installation: checking all kernels...
Building only for 4.6.0-040600rc7-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc7-generic

```

```
andrea@laptop-andrea:~$ cat /var/lib/dkms/nvidia-364/364.19/build/make.log
DKMS make.log for nvidia-364-364.19 for kernel 4.6.0-040600rc7-generic (x86_64)
ven 13 mag 2016, 15.52.09, CEST
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.6.0-040600rc7-generic/build M=/var/lib/dkms/nvidia-364/364.19/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.6.0-040600rc7-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: ingresso nella directory "/usr/src/linux-headers-4.6.0-040600rc7-generic"
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia-modeset/nv-modeset-kernel.o
 CONFTEST: INIT_WORK
 CONFTEST: remap_pfn_range
 CONFTEST: set_memory_uc
 CONFTEST: set_pages_uc
 CONFTEST: vmap
 CONFTEST: follow_pfn
 CONFTEST: set_memory_array_uc
 CONFTEST: change_page_attr
andrea@laptop-andrea:~$
```

it's about the same, this time it stops some rows before the last time in the make.log

(booted up with 4.2 kernel, purged 4.6 kernel, rebooted, installed kernel that you linked above, rebooted again, try to install nvidia-364 again)

---

### Post by 9600xt on 2016-05-16
Quiet the same with Kernel 4.6.0 final

```
andrea@laptop-andrea:~$ sudo apt-get install --reinstall nvidia-364 bumblebee primus libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 mesa-utils xserver-xorg-video-intelLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
The following additional packages will be installed:
  libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dev libglapi-mesa
  libglapi-mesa:i386 libgles1-mesa libgles2-mesa libgles2-mesa-dbg
  libgles2-mesa-dev libosmesa6 libosmesa6:i386 libwayland-egl1-mesa
  mesa-common-dev
I seguenti pacchetti NUOVI saranno installati:
  nvidia-364
I seguenti pacchetti saranno aggiornati:
  libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa
  libglapi-mesa:i386 libgles1-mesa libgles2-mesa libgles2-mesa-dbg
  libgles2-mesa-dev libosmesa6 libosmesa6:i386 libwayland-egl1-mesa
  mesa-common-dev
18 aggiornati, 1 installati, 4 reinstallati, 0 da rimuovere e 3 non aggiornati.
È necessario scaricare 82,6 MB/84,4 MB di archivi.
Dopo quest'operazione, verranno occupati 303 MB di spazio su disco.
Continuare? [S/n] S
Scaricamento di:1 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libegl1-mesa-dev amd64 11.3~git1605160730.9525f3~gd~x [58,5 kB]
Scaricamento di:2 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libwayland-egl1-mesa amd64 11.3~git1605160730.9525f3~gd~x [46,7 kB]
Scaricamento di:3 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgbm1 amd64 11.3~git1605160730.9525f3~gd~x [64,0 kB]
Scaricamento di:4 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libegl1-mesa amd64 11.3~git1605160730.9525f3~gd~x [113 kB]
Scaricamento di:5 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main i386 libgl1-mesa-dri i386 11.3~git1605160730.9525f3~gd~x [5.101 kB]
Scaricamento di:6 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgl1-mesa-dri amd64 11.3~git1605160730.9525f3~gd~x [4.999 kB]
Scaricamento di:7 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgl1-mesa-dev amd64 11.3~git1605160730.9525f3~gd~x [45,4 kB]
Scaricamento di:8 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 mesa-common-dev amd64 11.3~git1605160730.9525f3~gd~x [508 kB]
Scaricamento di:9 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main i386 libosmesa6 i386 11.3~git1605160730.9525f3~gd~x [1.188 kB]
Scaricamento di:10 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libosmesa6 amd64 11.3~git1605160730.9525f3~gd~x [1.204 kB]
Scaricamento di:11 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgles2-mesa-dbg amd64 11.3~git1605160730.9525f3~gd~x [49,0 kB]
Scaricamento di:12 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgles2-mesa-dev amd64 11.3~git1605160730.9525f3~gd~x [74,5 kB]
Scaricamento di:13 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgles2-mesa amd64 11.3~git1605160730.9525f3~gd~x [52,8 kB]
Scaricamento di:14 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgles1-mesa amd64 11.3~git1605160730.9525f3~gd~x [49,8 kB]
Scaricamento di:15 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main i386 libgl1-mesa-glx i386 11.3~git1605160730.9525f3~gd~x [162 kB]
Scaricamento di:16 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libgl1-mesa-glx amd64 11.3~git1605160730.9525f3~gd~x [164 kB]
Scaricamento di:17 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main amd64 libglapi-mesa amd64 11.3~git1605160730.9525f3~gd~x [62,6 kB]
Scaricamento di:18 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial/main i386 libglapi-mesa i386 11.3~git1605160730.9525f3~gd~x [62,9 kB]
Scaricamento di:19 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 nvidia-364 amd64 364.19-0ubuntu0~gpu16.04.3 [68,6 MB]
Recuperati 82,6 MB in 1min 14s (1.104 kB/s)                                    
(Lettura del database... 411620 file e directory attualmente installati.)
Preparativi per estrarre .../bumblebee_3.2.1-10_amd64.deb...
Estrazione di bumblebee (3.2.1-10) su (3.2.1-10)...
Preparativi per estrarre .../libegl1-mesa-dev_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libegl1-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libwayland-egl1-mesa_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libwayland-egl1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgbm1_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgbm1:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libegl1-mesa_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libegl1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605160730.9525f3~gd~x_amd64.deb...
De-configurazione di libgl1-mesa-dri:i386 (11.3~git1605151930.9323d0~gd~x)...
Estrazione di libgl1-mesa-dri:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-dri_11.3~git1605160730.9525f3~gd~x_i386.deb...
Estrazione di libgl1-mesa-dri:i386 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-dev_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgl1-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../mesa-common-dev_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di mesa-common-dev:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libosmesa6_11.3~git1605160730.9525f3~gd~x_amd64.deb...
De-configurazione di libosmesa6:i386 (11.3~git1605151930.9323d0~gd~x)...
Estrazione di libosmesa6:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libosmesa6_11.3~git1605160730.9525f3~gd~x_i386.deb...
Estrazione di libosmesa6:i386 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgles2-mesa-dbg_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgles2-mesa-dbg:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgles2-mesa-dev_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgles2-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgles2-mesa_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgles2-mesa:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgles1-mesa_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libgles1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605160730.9525f3~gd~x_amd64.deb...
De-configurazione di libgl1-mesa-glx:i386 (11.3~git1605151930.9323d0~gd~x)...
Estrazione di libgl1-mesa-glx:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libgl1-mesa-glx_11.3~git1605160730.9525f3~gd~x_i386.deb...
Estrazione di libgl1-mesa-glx:i386 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libglapi-mesa_11.3~git1605160730.9525f3~gd~x_i386.deb...
De-configurazione di libglapi-mesa:amd64 (11.3~git1605151930.9323d0~gd~x)...
Estrazione di libglapi-mesa:i386 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Preparativi per estrarre .../libglapi-mesa_11.3~git1605160730.9525f3~gd~x_amd64.deb...
Estrazione di libglapi-mesa:amd64 (11.3~git1605160730.9525f3~gd~x) su (11.3~git1605151930.9323d0~gd~x)...
Selezionato il pacchetto nvidia-364 non precedentemente selezionato.
Preparativi per estrarre .../nvidia-364_364.19-0ubuntu0~gpu16.04.3_amd64.deb...
Estrazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.3)...
Preparativi per estrarre .../xserver-xorg-video-intel_2%3a2.99.917+git1605091646.88733a~gd~x_amd64.deb...
Estrazione di xserver-xorg-video-intel (2:2.99.917+git1605091646.88733a~gd~x) su (2:2.99.917+git1605091646.88733a~gd~x)...
Preparativi per estrarre .../mesa-utils_8.3.0-1_amd64.deb...
Estrazione di mesa-utils (8.3.0-1) su (8.3.0-1)...
Preparativi per estrarre .../primus_0~20150328-1_amd64.deb...
Estrazione di primus (0~20150328-1) su (0~20150328-1)...
Elaborazione dei trigger per initramfs-tools (0.122ubuntu8)...
update-initramfs: Generating /boot/initrd.img-4.6.0-040600-generic
Elaborazione dei trigger per man-db (2.7.5-1)...
Elaborazione dei trigger per systemd (229-4ubuntu5)...
Elaborazione dei trigger per ureadahead (0.100.0-19)...
Elaborazione dei trigger per libc-bin (2.23-0ubuntu3)...
Configurazione di bumblebee (3.2.1-10)...
Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
edit the BusID line in /etc/bumblebee/xorg.conf.nouveau .
insserv: warning: script 'douane' missing LSB tags and overrides
Configurazione di libgl1-mesa-dri:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgl1-mesa-dri:i386 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgbm1:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libegl1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libwayland-egl1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libegl1-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di mesa-common-dev:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libglapi-mesa:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libglapi-mesa:i386 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgl1-mesa-glx:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgl1-mesa-glx:i386 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgl1-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libosmesa6:i386 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libosmesa6:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgles2-mesa:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgles2-mesa-dbg:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgles2-mesa-dev:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di libgles1-mesa:amd64 (11.3~git1605160730.9525f3~gd~x)...
Configurazione di nvidia-364 (364.19-0ubuntu0~gpu16.04.3)...
update-alternatives: viene usato /usr/lib/nvidia-364/ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica
update-alternatives: viene usato /usr/lib/nvidia-364/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in modalità automatica
update-alternatives: viene usato /usr/share/nvidia-364/glamor.conf per fornire /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in modalità automatica
INFO:Enable nvidia-364
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Aggiunta dell'utente di sistema «nvidia-persistenced» (UID 117) ...
Aggiunta del nuovo gruppo «nvidia-persistenced» (GID 128) ...
Aggiunta del nuovo utente «nvidia-persistenced» (UID 117) con gruppo «nvidia-persistenced» ...
La directory home «/» non è stata creata.
Loading new nvidia-364-364.19 DKMS files...
First Installation: checking all kernels...
Building only for 4.6.0-040600-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600-generic
```

```
andrea@laptop-andrea:~$ cat /var/lib/dkms/nvidia-364/364.19/build/make.log
DKMS make.log for nvidia-364-364.19 for kernel 4.6.0-040600-generic (x86_64)lun 16 mag 2016, 09.31.22, CEST
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.6.0-040600-generic/build M=/var/lib/dkms/nvidia-364/364.19/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.6.0-040600-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.6.0-040600-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: ingresso nella directory "/usr/src/linux-headers-4.6.0-040600-generic"
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-364/364.19/build/nvidia-modeset/nv-modeset-kernel.o
andrea@laptop-andrea:~$
```

---

### Post by 9600xt on 2016-05-18
I created a post on the official nvidia linux dev forum [here]("https://devtalk.nvidia.com/default/topic/936239/linux/ubuntu-16-04-all-kernel-version-stucks-while-building-dkms-module/") , and someone wrote this:

> [COLOR=#333333][FONT=DINWebPro]I'm going to guess this has something to do with the 860m identifier string being missing from some internal list of GPUs since it was one of those weird between-generations GPUs.[/FONT][/COLOR]

so to do a test I thinked to try to install an older driver version, so i did with 340.96 that was patched some hours ago to support kernel 4.6.0 too, and this was the result:
 
```
Loading new nvidia-340-340.96 DKMS files...First Installation: checking all kernels...
Building only for 4.6.0-040600-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600-generic
Done.


nvidia_340:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.6.0-040600-generic/updates/dkms/


nvidia_340_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.6.0-040600-generic/updates/dkms/


depmod....


DKMS: install completed.
dpkg: errore nell'elaborare il pacchetto nvidia-340 (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 10
```

this time the dkms do not stuck!!!! but, at the end, there is some error again...

Maybe 340.96 are too old driver for my gtx 860m?? 

@ricotz
Please apply the kernel patch on PPA to 346.96, 352.79, 355.11 and 358.16 driver version, so I can make some more test!

@Alberto Milone
the script that fails at the end, post-installation script, if i'm not wrong, was written by you...

---

