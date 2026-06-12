---
title: "What determines auto voltage with amdgpu [RX 580]"
date: 2020-04-10
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2020-04-10
I have 2 RX 580s that i can test at the moment
One is a early model released by gigabyte (not a good stock cooling design) and the other is a popular model Sapphire nitro plus
When i use the Sapphire card it automatically uses 1131mV, but the gigabyte card gets 1200 mV shoved into the core
if i open the vBIOS of both cards in a bios editor they have the same voltage configs with the only difference being the max clock speed (factory OC vBIOS)
in windows the sapphire card gets 1131mV at full clock speed while the gigabyte cards gets 1150mV
the only thing i can guess is the driver has a card lookup table and uses that to apply stock voltage and if there is no entry it goes with the max supported voltage (as in the max you can apply when overclocking without modifying the vBIOS or using a hardmod)

the only way i have to get a correct voltage on the gigabyte card is to use the overclocking feature ans insert a correct voltage, my testing shows 1100mV was enough to run at stock clock speeds

---

