---
title: "Help with missing drivers - Ryzen laptop"
date: 2020-10-27
forum: Hardware
---

### Post by blackbird34 on 2020-10-27
Hi everyone,

I was just reading a Jim Salter review of a Ryzen laptop and he mentioned a command to detect unsupported hardware. What do I need to install on my laptop (MSI Modern 14 with an AMD Ryzen 5 4500U) and how can I get it?

(I've been having problems getting the laptop to sleep: when it resumes, it hangs in an unusable state and I have to hold the power button down for 10s to turn it off. Plus various backlight-related errors and bugs)

```

[FONT=monospace][COLOR=#000000]sudo lshw | grep -A4 -B4 -i unclaimed  [/COLOR]
          bus info: pci@0000:00:00.0 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
        *-generic [COLOR=#ff5454]**UNCLAIMED**[/COLOR][COLOR=#000000] [/COLOR]
             description: IOMMU 
             product: Renoir IOMMU 
             vendor: Advanced Micro Devices, Inc. [AMD] 
             physical id: 0.2 
[COLOR=#18b2b2]--[/COLOR][COLOR=#000000] [/COLOR]
                   logical name: usb4 
                   version: 5.08 
                   capabilities: usb-3.10 
                   configuration: driver=hub slots=2 speed=10000Mbit/s 
           *-multimedia:1 [COLOR=#ff5454]**UNCLAIMED**[/COLOR][COLOR=#000000] [/COLOR]
                description: Multimedia controller 
                product: Raven/Raven2/FireFlight/Renoir Audio Processor 
                vendor: Advanced Micro Devices, Inc. [AMD] 
                physical id: 0.5
[/FONT]
```

---

### Post by Yellow Pasque on 2020-10-29
Don't worry about the IOMMU being unclaimed. As for the audio, you probably need a newer kernel for that to work. But if you don't need to use the HDMI/DP audio, don't worry about that either.

---

### Post by tflovik on 2020-10-30
Is the bios set to use UEFI or legacy?
If set to legacy you can get a lot of problems, but might need to reinstall after setting it to UEFI if it was set to legacy.

---

### Post by The Cog on 2020-10-30
I had terrible problems with my shiny new Ryzen 4700U until I upgraded the kernel. Now it's perfect. I read on Phoronx that the 4700 Renoir drivers were only in the 5.8.kernel - later than anything Ubuntu comes with. I'm on kernel 5.9.1 right now.
I don't know about the 4500 but it may be worth trying a newer kernel. Here are some links:
[https://www.tecmint.com/upgrade-kernel-in-ubuntu/](https://www.tecmint.com/upgrade-kernel-in-ubuntu/)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
Find the version you want, and download the debs except the low-latency ones. Then install them with "sudo dpkg -i *deb".
Hope this helps.

---

### Post by blackbird34 on 2020-11-01
> **tflovik said:**
> Is the bios set to use UEFI or legacy?
If set to legacy you can get a lot of problems, but might need to reinstall after setting it to UEFI if it was set to legacy.

Oh no... I was worried and set it to legacy. So dumb of me. I hadn't needed to install a system for years, and even when I did, my previous laptop didn't seem to care either way, everything worked.

If I set the bios to UEFI and reinstall system, would that affect my NTFS data partition or would it remain usable?

PS i avoided most other kernel problems by running Manjaro and Kubuntu 20.10 on it, both have the 5.8 kernel out of the box.

---

### Post by MartyBuntu on 2020-11-01
Are you dual booting with Windows?

---

### Post by blackbird34 on 2020-11-02
No. The NTFS partition was just for data, and i chose NTFS for the data partition and left empty space in case I wanted Windows later. I bought the computer without an OS. It came with a partition full of Windows which I want to keep.

> If set to legacy you can get a lot of problems, but might need to reinstall after setting it to UEFI if it was set to legacy.

I think tflovik must be right, the issue must be UEFI related, which means a reinstall is necessary. Whenever I get round to it. Hibernate works even if sleep doesn't, so I think I'll just put up with the issue for now. Thanks everyone for your knowledge, much more friendly answers than the Manjaro forum :)

---

### Post by blackbird34 on 2021-03-03
Update: I just updated my BIOS following MSI's instructions (there was a new BIOS file published 2 weeks ago:x) and now suspend AND my trackpad work perfectly. No more workarounds. No more problems. Yay.

---

