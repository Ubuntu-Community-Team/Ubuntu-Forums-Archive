---
title: "Kernel Panic on Opteron install"
date: 2008-09-19
forum: Hardware
---

### Post by billymcc99 on 2008-09-19
Hello,

I have a new server, (new to me) it is a refurb from geeks.com here is a link to a listing of all the specs.

the servers memory tests fine, it also runs the 32 bit load just fine. But when i try to install the 64bit version i get a kernel panic. 

Any ideas?

Billy

---

### Post by IntuitiveNipple on 2008-09-19
Hi Billy.

If I recall correctly you said on IRC that this happens with a 64-bit install but not 32-bit? (Excuse me if I've got this issue confused with some other!).

If so, can you boot the 32-bit version and then report the results of:
```

lspci -nn

lsusb

```
And attach a (compressed) copy of /var/log/dmesg to a reply:
```

cd ~
cat /var/log/dmesg | gzip > dmesg.log.gz

```

---

### Post by billymcc99 on 2008-09-19
Here are the 3 files you requested,

---

### Post by IntuitiveNipple on 2008-09-19
From the dmesg report it suggests the PC has more than 4GB of RAM installed?

If so, try reducing the installed RAM to 2GB as a test. If that starts, increase to 4GB and try again.

---

### Post by billymcc99 on 2008-09-19
i just noticed under 32bit, Ubuntu, i only see 2 gig of the 4, based on free -g and top... 

that seems weird?

---

### Post by IntuitiveNipple on 2008-09-19
The message is generated in arch/x86/kernel/head_64.S::early_idt_handler() 
```

ENTRY(early_idt_handler)
	cmpl $2,early_recursion_flag(%rip)
	jz  1f
	incl early_recursion_flag(%rip)
	xorl %eax,%eax
	movq 8(%rsp),%rsi	# get rip
	movq (%rsp),%rdx
	movq %cr2,%rcx
	leaq early_idt_msg(%rip),%rdi
	call early_printk
	cmpl $2,early_recursion_flag(%rip)
	jz  1f
	call dump_stack
#ifdef CONFIG_KALLSYMS	
	leaq early_idt_ripmsg(%rip),%rdi
	movq 8(%rsp),%rsi	# get rip again
	call __print_symbol
#endif
1:	hlt
	jmp 1b
early_recursion_flag:
	.long 0

early_idt_msg:
	.asciz "PANIC: early exception rip %lx error %lx cr2 %lx\n"
early_idt_ripmsg:
	.asciz "RIP %s\n"

```
which is called from arch/x86/kernel/head64.c x86_64_start_kernel()
```
void __init x86_64_start_kernel(char * real_mode_data)
{
	int i;

	/* clear bss before set_intr_gate with early_idt_handler */
	clear_bss();

	/* Make NULL pointers segfault */
	zap_identity_mappings();

	for (i = 0; i < IDT_ENTRIES; i++)
		set_intr_gate(i, early_idt_handler);
	load_idt((const struct desc_ptr *)&idt_descr);

	early_printk("Kernel alive\n");

```

---

### Post by billymcc99 on 2008-09-19
Same Kernel panic under 2 gig as 4 on 64bit iso.

---

### Post by IntuitiveNipple on 2008-09-19
> **billymcc99 said:**
> i just noticed under 32bit, Ubuntu, i only see 2 gig of the 4, based on free -g and top... 

that seems weird?
According to dmesg it's using more than that:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7fd0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7fd0000 - 00000000b7fde000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7fde000 - 00000000b8000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000145000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

```

---

### Post by billymcc99 on 2008-09-19
Sorry, im not sure what all that means?

---

### Post by IntuitiveNipple on 2008-09-19
I'm trying to pin-point the source of the issue for you. It sounds as if you'll need to search the launchpad bug reports for something similar. If you can't find anything report a new bug against the "linux" package.

---

### Post by billymcc99 on 2008-09-19
My goal for this machine is to be a workhorse/workstation for vmware virutals, i do a lot of consulting with vmware, and am constantly building virutals.

So i looked for a dual proc machine with ram capablitiies north of 4 gig (this one can do 16) 

is it worth my while to do the 64bit os? Or just stay with 32? and wondery why the 32 is not reporting all the ram in free and top?

-Billy

---

### Post by IntuitiveNipple on 2008-09-19
It looks like you're not alone:

[Bug #54020: Kernel panic on install on amd64](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54020)

Add a comment to that bug with the lspci -nn report (as text) and a link to this thread so others can find information.

---

### Post by billymcc99 on 2008-09-19
Yes that sounds very much like what im dealing with... 

Thaks so much for your help, any parting ideas as to what i should do next?

-Billy

---

### Post by IntuitiveNipple on 2008-09-19
I'll do some digging see what I can discover. I'm in the kernel ACPI team and this isn't too far off what I focus on so I may find something useful. I'd suggest you use the forum tools to subscribe to this thread so you get instant email notification of any replies. If you comment on that bug you should get emails when new comments are posted there, too.

I'll do the same and add information to the bug report if I find any.

---

