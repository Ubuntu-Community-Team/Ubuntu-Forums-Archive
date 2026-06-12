---
title: "ACPI kernel Oops, how do I load ath_pci?"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by nik_nah on 2007-09-08
I am using an acer aspire 3002, 1gig of ram.  ACPI used to work fine on this machine I'm not sure if it's because of a recent update or because I upgraded my ram from 512meg to 1gig, but it's stopped working.

During startup I'm getting the below message(if I continue with loading the acpi modules after this it'll halt during "ac" or "thermal")


[   26.496111] Capability LSM initialized
[   26.509164] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   26.537997] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   26.538654] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[   26.538660]  printing eip:
[   26.538662] c02db3c1
[   26.538664] *pde = 00000000
[   26.538668] Oops: 0002 [#1]
[   26.538670] Modules linked in: thermal processor fan dm_mod capability commoncap vesafb fbcon tileblit font bitblit softcursor
[   26.538680] CPU:    0
[   26.538681] EIP:    0060:[<c02db3c1>]    Not tainted VLI
[   26.538683] EFLAGS: 00010296   (2.6.20-16-386 #2)
[   26.538691] EIP is at __mutex_lock_slowpath+0x21/0x70
[   26.538695] eax: ffffffff   ebx: f6444e98   ecx: 00000000   edx: 00000000
[   26.538698] esi: 00000001   edi: dff9a030   ebp: f6444e9c   esp: dff09ad8
[   26.538701] ds: 007b   es: 007b   ss: 0068
[   26.538705] Process modprobe (pid: 1222, ti=dff08000 task=dff9a030 task.ti=dff08000)
[   26.538707] Stack: f6444e9c 00000000 6c381000 f6444e98 00000001 dff09b48 dff09b40 c02db2e3 
[   26.538714]        f6444e80 c020d6a1 cccc0000 cccccc00 80cccccc f6444e98 00000000 00000000 
[   26.538720]        00000000 00000000 dff09b64 00000000 00000000 00000058 c020d933 00000001 
[   26.538725] Call Trace:
[   26.538728]  [<c02db2e3>] mutex_lock+0x13/0x20
[   26.538733]  [<c020d6a1>] acpi_ec_transaction+0x69/0x1ba
[   26.538740]  [<c020d933>] acpi_ec_read+0x2f/0x3a
[   26.538745]  [<c020d9dc>] acpi_ec_space_handler+0x9e/0x186
[   26.538751]  [<c020d93e>] acpi_ec_space_handler+0x0/0x186
[   26.538755]  [<c01f8f34>] acpi_ev_address_space_dispatch+0x16c/0x1b9
[   26.538761]  [<c01fcfb3>] acpi_ex_access_region+0x224/0x23c
[   26.538767]  [<c01fd0de>] acpi_ex_field_datum_io+0x113/0x1a7
[   26.538771]  [<c011fae6>] current_fs_time+0x46/0x50
[   26.538777]  [<c01fd21b>] acpi_ex_extract_from_field+0xa9/0x230
[   26.538781]  [<c014684a>] do_generic_mapping_read+0x42a/0x530
[   26.538788]  [<c020b4ab>] acpi_ut_allocate_object_desc_dbg+0x36/0x6d
[   26.538793]  [<c0209a9a>] acpi_ut_valid_acpi_name+0x15/0x2e
[   26.538797]  [<c0209a9a>] acpi_ut_valid_acpi_name+0x15/0x2e
[   26.538801]  [<c0202892>] acpi_ns_search_one_scope+0x12/0x37
[   26.538807]  [<c01fba6c>] acpi_ex_read_data_from_field+0x104/0x134
[   26.538812]  [<c0200dea>] acpi_ex_resolve_node_to_value+0x17a/0x220
[   26.538817]  [<c020b4ab>] acpi_ut_allocate_object_desc_dbg+0x36/0x6d
[   26.538822]  [<c01fc6e4>] acpi_ex_resolve_to_value+0x228/0x234
[   26.538827]  [<c01f75f2>] acpi_ds_create_operand+0x1ca/0x1d6
[   26.538833]  [<c01fe896>] acpi_ex_resolve_operands+0x23d/0x57f
[   26.538838]  [<c01f65a8>] acpi_ds_exec_end_op+0xb3/0x3cf
[   26.538843]  [<c0205969>] acpi_ps_append_arg+0x16/0x75
[   26.538847]  [<c0205604>] acpi_ps_parse_loop+0x5b0/0x8cc
[   26.538852]  [<c0204c6a>] acpi_ps_parse_aml+0x60/0x1ff
[   26.538856]  [<c01f862c>] acpi_ds_init_aml_walk+0xb4/0xfe
[   26.538860]  [<c0205d54>] acpi_ps_execute_pass+0x81/0x94
[   26.538864]  [<c0205e55>] acpi_ps_execute_method+0xbe/0x14d
[   26.538868]  [<c0203229>] acpi_ns_evaluate+0x9d/0xfc
[   26.538873]  [<c0202e81>] acpi_evaluate_object+0x139/0x1e0
[   26.538878]  [<c01f4bf9>] acpi_evaluate_integer+0x80/0xb3
[   26.538883]  [<f885b09e>] acpi_thermal_get_temperature+0x2b/0x38 [thermal]
[   26.538889]  [<f885becb>] acpi_thermal_add+0x89/0x308 [thermal]
[   26.538896]  [<c02102b5>] acpi_bus_driver_init+0x28/0x4b
[   26.538901]  [<c02108ec>] acpi_bus_register_driver+0x5a/0x7c
[   26.538905]  [<f882202f>] acpi_thermal_init+0x2f/0x4d [thermal]
[   26.538910]  [<c0136167>] sys_init_module+0x157/0x17c0
[   26.538919]  [<c0210892>] acpi_bus_register_driver+0x0/0x7c
[   26.538924]  [<c0103050>] syscall_call+0x7/0xb
[   26.538930]  =======================
[   26.538931] Code: 40 08 e9 33 d3 e3 ff 8d 76 00 55 57 56 53 89 c3 8d 68 04 83 ec 0c 8b 55 04 b8 ff ff ff ff 65 8b 3d 08 00 00 00 89 2c 24 89 65 04 <89> 22 89 54 24 04 89 7c 24 08 87 03 83 e8 01 74 19 be ff ff ff 
[   26.538954] EIP: [<c02db3c1>] __mutex_lock_slowpath+0x21/0x70 SS:ESP 0068:dff09ad8
[   26.538959]  <6>md: linear personality registered for level -1
[   26.611103] md: multipath personality registered for level -4
[   26.614523] md: raid0 personality registered for level 0
[   26.618410] md: raid1 personality registered for level 1




I don't really care about ACPI, I just want to use my wireless card which seems to need it. When I plug in my pccard (atheros), it just says...
[  224.100000] pccard: card ejected from slot 0
[  226.308000] pccard: CardBus card inserted into slot 0

...and nothing happens, no driver is loaded.   
What program is responsible for loading pccard driver?
How do I load ath_pci manually?  it seems to need ath_hal which doesn't have a module just some .o files.

---

