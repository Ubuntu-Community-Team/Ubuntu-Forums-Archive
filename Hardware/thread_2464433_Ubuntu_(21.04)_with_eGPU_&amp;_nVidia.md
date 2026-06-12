---
title: "Ubuntu (21.04) with eGPU &amp; nVidia"
date: 2021-07-01
forum: Hardware
---

### Post by gareaura on 2021-07-01
I am newish to Linux. I do know some but I'm no expert so please go easy.

I have spent 3 days sifting though forums, how to's and the likes trying to get a laptop to run Ubuntu with an eGPU via Thunderbolt 3 with no luck. And by no luck I mean I have made some progress however in the end, the system just hard locks after BIOS post.

My OS atm is Ubuntu 21.04. I am running nVidia drivers 460 via OS additional drivers.

1. Thunderbolt is recognized. When I navigate to the Privacy section of options under Ubuntu it shows its approved and connected.
    When I execute 'lspci' it is listed.
2. My GPU located in the eGPU box connected via Thunderbolt is also recognized, I can confirm this by loading the nVidia X Session manager and seeing it listed as Card 1 of 2. Card 0 being the dGPU.
    When I verify that the nVidia drivers are being used via "nvidia-smi' it also confirms they are in fact loaded.
    
Where things go south is when I select the eGPU connected via Thunderbolt in nVidia's X session manager and save changes to the system->reboot and well freezes every time.

---

