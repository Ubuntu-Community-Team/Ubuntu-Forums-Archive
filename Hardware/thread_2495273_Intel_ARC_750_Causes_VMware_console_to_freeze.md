---
title: "Intel ARC 750 Causes VMware console to freeze"
date: 2024-02-13
forum: Hardware
---

### Post by burrsg101 on 2024-02-13
Hello all,

I have an issue with one of my Ubuntu VMs running in ESXI 7.0 U3 that I'm hoping to get some help with. Backstory first:
I have a media server running within this Ubuntu VM that uses a GPU for  transcoding. I first ran an old P2000 Nvidia GPU which didn't support  codecs I wanted, so I tried an AMD MI25 which worked great, except my  media server didn't fully support it (go figure), so I've now ended on  the Intel ARC 750 GPU which transcodes great and is fully supported by  the media server software. These all have been utilized in a direct  passthrough setting in VMware.

Hardware is an HP ML350 Gen9 and everything is accessed through VMware  web console, and there are no monitors connected to the host. My Ubuntu  is 22.04.3 LTS running the generic 6.5 kernel (required to get the Intel  ARC drivers installed and operating) with a MATE desktop GUI.

My issue is that with the Intel ARC card it appears to be setting this  GPU as the default device and blocking the VMware vga adapter so I lose  console access as soon as it gets to the point in the boot. (See the  screenshot below, switching from 0000 to 0002). To my knowledge the 0000  device is the VMware VGA adapter that is required to display the vmware  console and the 0002 is the Intel ARC GPU, so when it switches I lose  display. If I remove the gpu from the VM in VMware I get my display back  just fine.  The console freezes at the point of this switch, but the VM  and everything associated (my media server included) are operating fine  still, I just have no display.

My question is this, is there anyway to make the VMware VGA device  remain as the default for display with the Intel GPU in the background  so to speak waiting to be utilized by my media server?

Thanks for any help in advance.

---

### Post by MAFoElffen on 2024-02-14
This is really a VMware Virtual Host question... But hey, why not.

On the HP ML350 Gen9 Xeon processors do not have an iGPU. That server supports GPU's as cards... Which you only mentioned the Intel ARC 750... What is your other GPU? If you are passing that one through, then you lose that for use by the host.

Do you not have another GPU? So that when the ARc is committed to the VM, that the host has something to use... 

EDIT: You said you had other GPU's on-hand, that you tried previously for our VM. They didn't work out for the passthrough to your VM for what you needed to do, but they could work for your Host right? I have even just used cheap x1 VGA only GPU's for host use, just soi I have "something." Just saying.

Otherwsie, if you were using KVM, instead of VMware, I would just tell you to use scripts in the hooks to unassign the GPU from the host and hand it over to the VM via vfio, then back to the host on exit. But you are using VMware, so can't do that, that way.

---

### Post by burrsg101 on 2024-02-14
Sorry, I may have been a bit muddy with my description here. There is no other GPU in the host aside from this ARC card. What I was referring to is a virtual VGA adapter that a hypervisor sets up when you create a VM so that you can view and control that VM from whatever interface your hypervisor contains. In this case with VMware I am running vCenter so I'm going through the web GUI. Without passing any actual GPU through into the VM, a VM views this virtual VGA adapter as its "GPU" so to speak. With the other 2 cards I had installed, Ubuntu left VMware's virtual VGA as the primary adapter so my VMware console functioned as it should. I suspect the difference here is that both of those cards are server GPUs, and this ARC is a consumer grade so it is treated differently by Ubuntu (this is just a guess on my part). 

In summary, I just need to find a way to make Ubuntu treat the VMware virtual VGA as its primary "GPU" again instead of handing that off to the ARC card during the boot process.

---

