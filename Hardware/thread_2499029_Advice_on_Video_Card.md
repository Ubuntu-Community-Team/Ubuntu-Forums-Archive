---
title: "Advice on Video Card"
date: 2024-07-08
forum: Hardware
---

### Post by gary-cit-solutions on 2024-07-08
Hello

For years I have always used NVidia cards in my Ubuntu PCs (last 10 + years), I found they performed well in gaming and were stable, I had the odd glitch when installing new drivers but was easily sorted

I bought myself a Dell 8960 i9-13900K with 32Gb RAM and an RTX 4080...it works beautifully super fast with latest Ubuntu*BUT* there are only 3 X PCI-E Card Slots and the RTX 4080 is so wide it covers them ALL (cant believe DELL Sold this and also the fact I didn't notice) so I have no free PCI-E slots which is a problem as I cannot install my 10G Fibre Network card and am getting fed up with the slow 1Gb Ethernet speed as I transfer large files to and from my Server

The machine is primarily an all purpose Desktop PC (3 Monitors running Chrome/Gnumeric/VS Code - just every day tasks but I do shunt large ESXI and ISO Files about) but I do play the occasional Steam game

I was thinking of replacing my RTX 4080 with an AMD 7000 GRE which will free up the one slot I need

My question is how good is AMD at gaming on Ubuntu these days (I do know it is a slower card so do expect some performance loss obviously...but it is mostly older games I play eg counterstrike) ...is it Stable and efficient (I last used AMD 7+ years ago with Nouveau drivers I think they were called and the gaming performance was so poor VS NVidia's prop drivers

All advice greatly appreciated

Thanks in advance

Gary

---

### Post by Shibblet on 2024-07-08
AMD Cards work great...  but you're going to be hard pressed to find one better than a GTX4080.

Have you considered a PCI extension cable?

[https://www.amazon.com/Okinos-Extension-Compatible-RTX4070ti-RTX3090ti/dp/B0C22WJTMB/ref=sr_1_3?dib=eyJ2IjoiMSJ9.hCGf_X210aNnNOqz1Q_oPdBUsPW7wKPOze90c6-aQgpRPzQ4-UdAh8P_XcnRIZezl2b-Rq-PXQReP3cueCxoi-nLNcdFMbuCH3tHQkj6wrYe5rzPjKooTa9_3ONEiK-tdeZ7p0kDSQ9g-HVxfE2Zc3EcAB-j63EKTHIS6x9xykL9bNXX08EOE0hBU9UndJBUoarSGDpCuy_X_2K-uEc5iBfsv22cYc6ggbZyKyTQbS8.uHShf-bfXoY1msy1NUl9lxvLhgmS7firHocEQ3I-slQ&dib_tag=se&keywords=pcie+extension+cable&qid=1720472799&sr=8-3]("https://www.amazon.com/Okinos-Extension-Compatible-RTX4070ti-RTX3090ti/dp/B0C22WJTMB/ref=sr_1_3?dib=eyJ2IjoiMSJ9.hCGf_X210aNnNOqz1Q_oPdBUsPW7wKPOze90c6-aQgpRPzQ4-UdAh8P_XcnRIZezl2b-Rq-PXQReP3cueCxoi-nLNcdFMbuCH3tHQkj6wrYe5rzPjKooTa9_3ONEiK-tdeZ7p0kDSQ9g-HVxfE2Zc3EcAB-j63EKTHIS6x9xykL9bNXX08EOE0hBU9UndJBUoarSGDpCuy_X_2K-uEc5iBfsv22cYc6ggbZyKyTQbS8.uHShf-bfXoY1msy1NUl9lxvLhgmS7firHocEQ3I-slQ&dib_tag=se&keywords=pcie+extension+cable&qid=1720472799&sr=8-3")

---

### Post by currentshaft on 2024-07-08
You need what's known as a riser cable. Maybe a new case which supports XL graphics cards, too.

I am morbidly curious what you're transfering that needs >1G networking however.

---

### Post by gary-cit-solutions on 2024-07-09
Hi many thanks for the replies, here is a guy with the exact same problem !

[https://www.reddit.com/r/XPS/comments/184pzy6/a_big_problem_with_dell_xps_8960_and_pci_slots/](https://www.reddit.com/r/XPS/comments/184pzy6/a_big_problem_with_dell_xps_8960_and_pci_slots/)

I just realized I think that AMD card is too big as well, will have to do more research, I'm not too fussed about losing gaming performance as I only play older games (infrequently) and at lower resolutions, no 4K etc...such a bad design by Dell

I copy large disk image files up and down from my PC to the Server, these can be from 40Gb to 1Tb+ and you do notice the big difference in speed..I do have an ESXI Server but do some Virtual Machine workloads on my Local PC as well

I might have a look at that Extender Cable (Will have to wrap the NIC in an antistatic bag to prevent shorts I guess !)

---

### Post by TheFu on 2024-07-09
Unrelated but you are aware that VMware isn't giving ESXi away anymore and isn't interested in small businesses as clients.  [https://www.clouvider.com/knowledge_base/vmware-esxi-end-of-general-availability/](https://www.clouvider.com/knowledge_base/vmware-esxi-end-of-general-availability/) ESXi, all license version, have been pulled by Broadcom.

It is time to switch to a different hypervisor, unless you earn your living from VMware clients paying lots of money to VMware, there are lots of great options, including the F/LOSS hypervisors that are used by effectively all VPS providers in the world, including Amazon.  Just sayin'.

A few years ago now, I swapped a mid-level Ryzen for a newer Ryzen with an iGPU and removed a cheap nVidia GPU that was having driver issues. Seems all my nVidia cards have driver issues and get support pulled while I'm still using them, so I decided it made more sense to take my money anywhere else.  For high-end gamers with $1000 to spend on a GPU, I think you are stuck with nVidia.  If you are happy with mid- and low-tier performance, there's little reason to choose nvidia stuff.  AMD drivers have been built-into the kernel for a few years now.  I never think about them. They just work.  I have 2 Ryzen systems with iGPUs and those are faster than the cheap nvidia GPU I had before - not really a fair comparison, since the AMD iGPUs were 4 yrs newer than the nvidia card.  I paid $70 for that nvidia card when it was new, but could have sold it for $140 at the peak of GPU availability. I missed that, so it sits on a shelf here with my other "backup" GPUs to be used for testing when something fails in a computer.

None of this is relevant to your needs, since you are clearly wanting a $300+ GPU, which I've never bought and can't imagine ever owning. We are different types of users, clearly.

---

### Post by currentshaft on 2024-07-09
For midtier and low-end gaming, AMD cards offer the best value.

But AMD cards are about a decade behind NVIDIA in terms of AI performance.

For me that was a massive deal-breaker and I upgraded my 7900XT to an RTX 4090. Both cards run well in Ubuntu with no additional drivers.

---

