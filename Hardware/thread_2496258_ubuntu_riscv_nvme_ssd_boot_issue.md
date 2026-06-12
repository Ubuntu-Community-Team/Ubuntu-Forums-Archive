---
title: "ubuntu riscv nvme ssd boot issue"
date: 2024-03-20
forum: Hardware
---

### Post by ctclmsn on 2024-03-20
I have a sifive unmatched running the ubuntu distro at this link ([https://ubuntu.com/download/risc-v](https://ubuntu.com/download/risc-v)). The machine is configured to boot over NVME from an M2 SSD. The system has been working fine for months, but last Monday the root partition mounted by ubuntu changed to the microSD storage. Ubuntu is still booting off the kernel installed on the SSD storage (yay for UEFI), but the root directory is microSD. I've been able to mount the partitions on the SSD and can access my data there. How do I configure the system boot to use the partition off the SSD storage instead of the microSD card?

Thanks in advance!

---

