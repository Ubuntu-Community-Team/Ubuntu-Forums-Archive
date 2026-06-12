---
title: "radeon driver problem!"
date: 2013-05-15
forum: Hardware
---

### Post by TheOne...more on 2013-05-15
hi every one, it's been long since i posted or replied here.

well the problem is this, i have an old, outdated ati radeon card, but it's working perfectly, and above all it's all i got, and there are no intentions to upgrade at the moment. it's a rv350 9550/256 Mb card, and it gives me some 5000 fps on glxgears and 500 on fgl_glxgears on older ubuntu using the ati driver.

now i decided to give precise pangolin a try, installed it. it was easier, i admit. yet the problem of graphics still looms typically as with each installation with an ati graphics card. i have 3d, yes...but i can not control the resolution at all. i have only two options, either 1024x768 or 800x600 and both at 60hz. on ati close source driver i could reath 85hz easily on higher resolutions. also the 3d is very very slow. here is an hint 

```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.338 FPS
300 frames in 5.0 seconds = 59.970 FPS
300 frames in 5.0 seconds = 59.980 FPS
300 frames in 5.0 seconds = 59.981 FPS
300 frames in 5.0 seconds = 59.976 FPS
300 frames in 5.0 seconds = 59.978 FPS

```


as you can see, i don't know what to do. and if any one can help, please do.

thanks.

---

### Post by tgalati4 on 2013-05-15
```
modinfo radeon
```

I'm not familiar with running in synchronized mode.  Perhaps running in that mode restricts the resolution.  Try turning it off and rerun your tests.  You will have to search for how to do that, because I don't know.  Perhaps a kernel switch, a module switch, or an xorg.conf setting.

---

### Post by TheOne...more on 2013-05-15
thank you tgalati4 for replying.

i'm not actually fully aware of what you'r trying to say. i ran the command that you suggested, and i don't know which value of which parameter did you mean as the command gave lots of parameters.

```
filename:       /lib/modules/3.2.0-41-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
license:        GPL and additional rights
description:    ATI Radeon
author:         Gareth Hughes, Keith Whitwell, others.
firmware:       radeon/R520_cp.bin
firmware:       radeon/RS600_cp.bin
firmware:       radeon/RS690_cp.bin
firmware:       radeon/R420_cp.bin
firmware:       radeon/R300_cp.bin
firmware:       radeon/R200_cp.bin
firmware:       radeon/R100_cp.bin
firmware:       radeon/RV710_me.bin
firmware:       radeon/RV710_pfp.bin
firmware:       radeon/RV730_me.bin
firmware:       radeon/RV730_pfp.bin
firmware:       radeon/RV770_me.bin
firmware:       radeon/RV770_pfp.bin
firmware:       radeon/RS780_me.bin
firmware:       radeon/RS780_pfp.bin
firmware:       radeon/RV670_me.bin
firmware:       radeon/RV670_pfp.bin
firmware:       radeon/RV635_me.bin
firmware:       radeon/RV635_pfp.bin
firmware:       radeon/RV620_me.bin
firmware:       radeon/RV620_pfp.bin
firmware:       radeon/RV630_me.bin
firmware:       radeon/RV630_pfp.bin
firmware:       radeon/RV610_me.bin
firmware:       radeon/RV610_pfp.bin
firmware:       radeon/R600_me.bin
firmware:       radeon/R600_pfp.bin
firmware:       radeon/R520_cp.bin
firmware:       radeon/RS600_cp.bin
firmware:       radeon/RS690_cp.bin
firmware:       radeon/R420_cp.bin
firmware:       radeon/R300_cp.bin
firmware:       radeon/R200_cp.bin
firmware:       radeon/R100_cp.bin
firmware:       radeon/SUMO2_me.bin
firmware:       radeon/SUMO2_pfp.bin
firmware:       radeon/SUMO_me.bin
firmware:       radeon/SUMO_pfp.bin
firmware:       radeon/SUMO_rlc.bin
firmware:       radeon/PALM_me.bin
firmware:       radeon/PALM_pfp.bin
firmware:       radeon/CYPRESS_rlc.bin
firmware:       radeon/CYPRESS_me.bin
firmware:       radeon/CYPRESS_pfp.bin
firmware:       radeon/JUNIPER_rlc.bin
firmware:       radeon/JUNIPER_me.bin
firmware:       radeon/JUNIPER_pfp.bin
firmware:       radeon/REDWOOD_rlc.bin
firmware:       radeon/REDWOOD_me.bin
firmware:       radeon/REDWOOD_pfp.bin
firmware:       radeon/CEDAR_rlc.bin
firmware:       radeon/CEDAR_me.bin
firmware:       radeon/CEDAR_pfp.bin
firmware:       radeon/R700_rlc.bin
firmware:       radeon/R600_rlc.bin
firmware:       radeon/RV710_me.bin
firmware:       radeon/RV710_pfp.bin
firmware:       radeon/RV730_me.bin
firmware:       radeon/RV730_pfp.bin
firmware:       radeon/RV770_me.bin
firmware:       radeon/RV770_pfp.bin
firmware:       radeon/RS780_me.bin
firmware:       radeon/RS780_pfp.bin
firmware:       radeon/RV670_me.bin
firmware:       radeon/RV670_pfp.bin
firmware:       radeon/RV635_me.bin
firmware:       radeon/RV635_pfp.bin
firmware:       radeon/RV620_me.bin
firmware:       radeon/RV620_pfp.bin
firmware:       radeon/RV630_me.bin
firmware:       radeon/RV630_pfp.bin
firmware:       radeon/RV610_me.bin
firmware:       radeon/RV610_pfp.bin
firmware:       radeon/R600_me.bin
firmware:       radeon/R600_pfp.bin
firmware:       radeon/CAYMAN_rlc.bin
firmware:       radeon/CAYMAN_mc.bin
firmware:       radeon/CAYMAN_me.bin
firmware:       radeon/CAYMAN_pfp.bin
firmware:       radeon/CAICOS_mc.bin
firmware:       radeon/CAICOS_me.bin
firmware:       radeon/CAICOS_pfp.bin
firmware:       radeon/TURKS_mc.bin
firmware:       radeon/TURKS_me.bin
firmware:       radeon/TURKS_pfp.bin
firmware:       radeon/BTC_rlc.bin
firmware:       radeon/BARTS_mc.bin
firmware:       radeon/BARTS_me.bin
firmware:       radeon/BARTS_pfp.bin
srcversion:     1195C43EB1B18EA8C9BE0BF
alias:          pci:v00001002d0000980Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009809sv*sd*bc*sc*i*
alias:          pci:v00001002d00009808sv*sd*bc*sc*i*
alias:          pci:v00001002d00009807sv*sd*bc*sc*i*
alias:          pci:v00001002d00009806sv*sd*bc*sc*i*
alias:          pci:v00001002d00009805sv*sd*bc*sc*i*
alias:          pci:v00001002d00009804sv*sd*bc*sc*i*
alias:          pci:v00001002d00009803sv*sd*bc*sc*i*
alias:          pci:v00001002d00009802sv*sd*bc*sc*i*
alias:          pci:v00001002d00009715sv*sd*bc*sc*i*
alias:          pci:v00001002d00009714sv*sd*bc*sc*i*
alias:          pci:v00001002d00009713sv*sd*bc*sc*i*
alias:          pci:v00001002d00009712sv*sd*bc*sc*i*
alias:          pci:v00001002d00009711sv*sd*bc*sc*i*
alias:          pci:v00001002d00009710sv*sd*bc*sc*i*
alias:          pci:v00001002d0000964Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000964Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000964Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000964Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000964Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009649sv*sd*bc*sc*i*
alias:          pci:v00001002d00009648sv*sd*bc*sc*i*
alias:          pci:v00001002d00009647sv*sd*bc*sc*i*
alias:          pci:v00001002d00009645sv*sd*bc*sc*i*
alias:          pci:v00001002d00009644sv*sd*bc*sc*i*
alias:          pci:v00001002d00009643sv*sd*bc*sc*i*
alias:          pci:v00001002d00009642sv*sd*bc*sc*i*
alias:          pci:v00001002d00009641sv*sd*bc*sc*i*
alias:          pci:v00001002d00009640sv*sd*bc*sc*i*
alias:          pci:v00001002d00009616sv*sd*bc*sc*i*
alias:          pci:v00001002d00009615sv*sd*bc*sc*i*
alias:          pci:v00001002d00009614sv*sd*bc*sc*i*
alias:          pci:v00001002d00009613sv*sd*bc*sc*i*
alias:          pci:v00001002d00009612sv*sd*bc*sc*i*
alias:          pci:v00001002d00009611sv*sd*bc*sc*i*
alias:          pci:v00001002d00009610sv*sd*bc*sc*i*
alias:          pci:v00001002d000095CFsv*sd*bc*sc*i*
alias:          pci:v00001002d000095CEsv*sd*bc*sc*i*
alias:          pci:v00001002d000095CDsv*sd*bc*sc*i*
alias:          pci:v00001002d000095CCsv*sd*bc*sc*i*
alias:          pci:v00001002d000095C9sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C7sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C6sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C5sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C4sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C2sv*sd*bc*sc*i*
alias:          pci:v00001002d000095C0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000959Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00009599sv*sd*bc*sc*i*
alias:          pci:v00001002d00009598sv*sd*bc*sc*i*
alias:          pci:v00001002d00009597sv*sd*bc*sc*i*
alias:          pci:v00001002d00009596sv*sd*bc*sc*i*
alias:          pci:v00001002d00009595sv*sd*bc*sc*i*
alias:          pci:v00001002d00009593sv*sd*bc*sc*i*
alias:          pci:v00001002d00009591sv*sd*bc*sc*i*
alias:          pci:v00001002d00009590sv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000958Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009589sv*sd*bc*sc*i*
alias:          pci:v00001002d00009588sv*sd*bc*sc*i*
alias:          pci:v00001002d00009587sv*sd*bc*sc*i*
alias:          pci:v00001002d00009586sv*sd*bc*sc*i*
alias:          pci:v00001002d00009583sv*sd*bc*sc*i*
alias:          pci:v00001002d00009581sv*sd*bc*sc*i*
alias:          pci:v00001002d00009580sv*sd*bc*sc*i*
alias:          pci:v00001002d0000955Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00009557sv*sd*bc*sc*i*
alias:          pci:v00001002d00009555sv*sd*bc*sc*i*
alias:          pci:v00001002d00009553sv*sd*bc*sc*i*
alias:          pci:v00001002d00009552sv*sd*bc*sc*i*
alias:          pci:v00001002d0000954Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000954Esv*sd*bc*sc*i*
alias:          pci:v00001002d00009542sv*sd*bc*sc*i*
alias:          pci:v00001002d00009541sv*sd*bc*sc*i*
alias:          pci:v00001002d00009540sv*sd*bc*sc*i*
alias:          pci:v00001002d00009519sv*sd*bc*sc*i*
alias:          pci:v00001002d00009517sv*sd*bc*sc*i*
alias:          pci:v00001002d00009515sv*sd*bc*sc*i*
alias:          pci:v00001002d00009511sv*sd*bc*sc*i*
alias:          pci:v00001002d0000950Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00009509sv*sd*bc*sc*i*
alias:          pci:v00001002d00009508sv*sd*bc*sc*i*
alias:          pci:v00001002d00009507sv*sd*bc*sc*i*
alias:          pci:v00001002d00009506sv*sd*bc*sc*i*
alias:          pci:v00001002d00009505sv*sd*bc*sc*i*
alias:          pci:v00001002d00009504sv*sd*bc*sc*i*
alias:          pci:v00001002d00009501sv*sd*bc*sc*i*
alias:          pci:v00001002d00009500sv*sd*bc*sc*i*
alias:          pci:v00001002d000094CDsv*sd*bc*sc*i*
alias:          pci:v00001002d000094CCsv*sd*bc*sc*i*
alias:          pci:v00001002d000094CBsv*sd*bc*sc*i*
alias:          pci:v00001002d000094C9sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C8sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C7sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C6sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C5sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C4sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C3sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C1sv*sd*bc*sc*i*
alias:          pci:v00001002d000094C0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000949Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000949Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000949Csv*sd*bc*sc*i*
alias:          pci:v00001002d00009498sv*sd*bc*sc*i*
alias:          pci:v00001002d00009495sv*sd*bc*sc*i*
alias:          pci:v00001002d00009491sv*sd*bc*sc*i*
alias:          pci:v00001002d00009490sv*sd*bc*sc*i*
alias:          pci:v00001002d0000948Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000948Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009489sv*sd*bc*sc*i*
alias:          pci:v00001002d00009488sv*sd*bc*sc*i*
alias:          pci:v00001002d00009487sv*sd*bc*sc*i*
alias:          pci:v00001002d00009480sv*sd*bc*sc*i*
alias:          pci:v00001002d0000947Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000947Asv*sd*bc*sc*i*
alias:          pci:v00001002d0000946Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000946Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009462sv*sd*bc*sc*i*
alias:          pci:v00001002d00009460sv*sd*bc*sc*i*
alias:          pci:v00001002d0000945Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000945Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000945Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009456sv*sd*bc*sc*i*
alias:          pci:v00001002d00009452sv*sd*bc*sc*i*
alias:          pci:v00001002d00009450sv*sd*bc*sc*i*
alias:          pci:v00001002d0000944Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000944Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000944Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000944Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009446sv*sd*bc*sc*i*
alias:          pci:v00001002d00009444sv*sd*bc*sc*i*
alias:          pci:v00001002d00009443sv*sd*bc*sc*i*
alias:          pci:v00001002d00009442sv*sd*bc*sc*i*
alias:          pci:v00001002d00009441sv*sd*bc*sc*i*
alias:          pci:v00001002d00009440sv*sd*bc*sc*i*
alias:          pci:v00001002d000094B9sv*sd*bc*sc*i*
alias:          pci:v00001002d000094B5sv*sd*bc*sc*i*
alias:          pci:v00001002d000094B4sv*sd*bc*sc*i*
alias:          pci:v00001002d000094B3sv*sd*bc*sc*i*
alias:          pci:v00001002d000094B1sv*sd*bc*sc*i*
alias:          pci:v00001002d000094A3sv*sd*bc*sc*i*
alias:          pci:v00001002d000094A1sv*sd*bc*sc*i*
alias:          pci:v00001002d000094A0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000940Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000940Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000940Asv*sd*bc*sc*i*
alias:          pci:v00001002d00009405sv*sd*bc*sc*i*
alias:          pci:v00001002d00009403sv*sd*bc*sc*i*
alias:          pci:v00001002d00009402sv*sd*bc*sc*i*
alias:          pci:v00001002d00009401sv*sd*bc*sc*i*
alias:          pci:v00001002d00009400sv*sd*bc*sc*i*
alias:          pci:v00001002d0000796Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000796Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000796Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000796Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007942sv*sd*bc*sc*i*
alias:          pci:v00001002d00007941sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000791Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000791Esv*sd*bc*sc*i*
alias:          pci:v00001002d00007835sv*sd*bc*sc*i*
alias:          pci:v00001002d00007834sv*sd*bc*sc*i*
alias:          pci:v00001002d00007297sv*sd*bc*sc*i*
alias:          pci:v00001002d00007293sv*sd*bc*sc*i*
alias:          pci:v00001002d00007291sv*sd*bc*sc*i*
alias:          pci:v00001002d00007290sv*sd*bc*sc*i*
alias:          pci:v00001002d0000728Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000728Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00007289sv*sd*bc*sc*i*
alias:          pci:v00001002d00007288sv*sd*bc*sc*i*
alias:          pci:v00001002d00007287sv*sd*bc*sc*i*
alias:          pci:v00001002d00007284sv*sd*bc*sc*i*
alias:          pci:v00001002d00007283sv*sd*bc*sc*i*
alias:          pci:v00001002d00007281sv*sd*bc*sc*i*
alias:          pci:v00001002d00007280sv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000724Asv*sd*bc*sc*i*
alias:          pci:v00001002d00007249sv*sd*bc*sc*i*
alias:          pci:v00001002d00007248sv*sd*bc*sc*i*
alias:          pci:v00001002d00007247sv*sd*bc*sc*i*
alias:          pci:v00001002d00007246sv*sd*bc*sc*i*
alias:          pci:v00001002d00007245sv*sd*bc*sc*i*
alias:          pci:v00001002d00007244sv*sd*bc*sc*i*
alias:          pci:v00001002d00007243sv*sd*bc*sc*i*
alias:          pci:v00001002d00007240sv*sd*bc*sc*i*
alias:          pci:v00001002d00007211sv*sd*bc*sc*i*
alias:          pci:v00001002d00007210sv*sd*bc*sc*i*
alias:          pci:v00001002d00007200sv*sd*bc*sc*i*
alias:          pci:v00001002d000071DEsv*sd*bc*sc*i*
alias:          pci:v00001002d000071DAsv*sd*bc*sc*i*
alias:          pci:v00001002d000071D6sv*sd*bc*sc*i*
alias:          pci:v00001002d000071D5sv*sd*bc*sc*i*
alias:          pci:v00001002d000071D4sv*sd*bc*sc*i*
alias:          pci:v00001002d000071D2sv*sd*bc*sc*i*
alias:          pci:v00001002d000071CEsv*sd*bc*sc*i*
alias:          pci:v00001002d000071CDsv*sd*bc*sc*i*
alias:          pci:v00001002d000071C7sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C6sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C5sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C4sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C3sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C2sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C1sv*sd*bc*sc*i*
alias:          pci:v00001002d000071C0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000719Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000719Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00007196sv*sd*bc*sc*i*
alias:          pci:v00001002d00007193sv*sd*bc*sc*i*
alias:          pci:v00001002d0000718Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000718Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000718Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000718Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000718Asv*sd*bc*sc*i*
alias:          pci:v00001002d00007188sv*sd*bc*sc*i*
alias:          pci:v00001002d00007187sv*sd*bc*sc*i*
alias:          pci:v00001002d00007186sv*sd*bc*sc*i*
alias:          pci:v00001002d00007183sv*sd*bc*sc*i*
alias:          pci:v00001002d00007181sv*sd*bc*sc*i*
alias:          pci:v00001002d00007180sv*sd*bc*sc*i*
alias:          pci:v00001002d0000715Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000715Esv*sd*bc*sc*i*
alias:          pci:v00001002d00007153sv*sd*bc*sc*i*
alias:          pci:v00001002d00007152sv*sd*bc*sc*i*
alias:          pci:v00001002d00007151sv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000714Asv*sd*bc*sc*i*
alias:          pci:v00001002d00007149sv*sd*bc*sc*i*
alias:          pci:v00001002d00007147sv*sd*bc*sc*i*
alias:          pci:v00001002d00007146sv*sd*bc*sc*i*
alias:          pci:v00001002d00007145sv*sd*bc*sc*i*
alias:          pci:v00001002d00007144sv*sd*bc*sc*i*
alias:          pci:v00001002d00007143sv*sd*bc*sc*i*
alias:          pci:v00001002d00007142sv*sd*bc*sc*i*
alias:          pci:v00001002d00007141sv*sd*bc*sc*i*
alias:          pci:v00001002d00007140sv*sd*bc*sc*i*
alias:          pci:v00001002d0000710Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000710Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000710Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000710Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000710Asv*sd*bc*sc*i*
alias:          pci:v00001002d00007109sv*sd*bc*sc*i*
alias:          pci:v00001002d00007108sv*sd*bc*sc*i*
alias:          pci:v00001002d00007106sv*sd*bc*sc*i*
alias:          pci:v00001002d00007105sv*sd*bc*sc*i*
alias:          pci:v00001002d00007104sv*sd*bc*sc*i*
alias:          pci:v00001002d00007103sv*sd*bc*sc*i*
alias:          pci:v00001002d00007102sv*sd*bc*sc*i*
alias:          pci:v00001002d00007101sv*sd*bc*sc*i*
alias:          pci:v00001002d00007100sv*sd*bc*sc*i*
alias:          pci:v00001002d000068FEsv*sd*bc*sc*i*
alias:          pci:v00001002d000068FAsv*sd*bc*sc*i*
alias:          pci:v00001002d000068F9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068F8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068F2sv*sd*bc*sc*i*
alias:          pci:v00001002d000068F1sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E5sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E4sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E1sv*sd*bc*sc*i*
alias:          pci:v00001002d000068E0sv*sd*bc*sc*i*
alias:          pci:v00001002d000068DEsv*sd*bc*sc*i*
alias:          pci:v00001002d000068DAsv*sd*bc*sc*i*
alias:          pci:v00001002d000068D9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068D8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068C9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068C8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068C7sv*sd*bc*sc*i*
alias:          pci:v00001002d000068C1sv*sd*bc*sc*i*
alias:          pci:v00001002d000068C0sv*sd*bc*sc*i*
alias:          pci:v00001002d000068BFsv*sd*bc*sc*i*
alias:          pci:v00001002d000068BEsv*sd*bc*sc*i*
alias:          pci:v00001002d000068BAsv*sd*bc*sc*i*
alias:          pci:v00001002d000068B9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068B8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068B0sv*sd*bc*sc*i*
alias:          pci:v00001002d000068A9sv*sd*bc*sc*i*
alias:          pci:v00001002d000068A8sv*sd*bc*sc*i*
alias:          pci:v00001002d000068A1sv*sd*bc*sc*i*
alias:          pci:v00001002d000068A0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000689Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000689Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000689Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000689Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00006899sv*sd*bc*sc*i*
alias:          pci:v00001002d00006898sv*sd*bc*sc*i*
alias:          pci:v00001002d0000688Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000688Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000688Asv*sd*bc*sc*i*
alias:          pci:v00001002d00006889sv*sd*bc*sc*i*
alias:          pci:v00001002d00006888sv*sd*bc*sc*i*
alias:          pci:v00001002d00006880sv*sd*bc*sc*i*
alias:          pci:v00001002d00006859sv*sd*bc*sc*i*
alias:          pci:v00001002d00006858sv*sd*bc*sc*i*
alias:          pci:v00001002d00006850sv*sd*bc*sc*i*
alias:          pci:v00001002d00006849sv*sd*bc*sc*i*
alias:          pci:v00001002d00006843sv*sd*bc*sc*i*
alias:          pci:v00001002d00006842sv*sd*bc*sc*i*
alias:          pci:v00001002d00006841sv*sd*bc*sc*i*
alias:          pci:v00001002d00006840sv*sd*bc*sc*i*
alias:          pci:v00001002d0000677Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00006779sv*sd*bc*sc*i*
alias:          pci:v00001002d00006778sv*sd*bc*sc*i*
alias:          pci:v00001002d00006772sv*sd*bc*sc*i*
alias:          pci:v00001002d00006771sv*sd*bc*sc*i*
alias:          pci:v00001002d00006770sv*sd*bc*sc*i*
alias:          pci:v00001002d00006768sv*sd*bc*sc*i*
alias:          pci:v00001002d00006767sv*sd*bc*sc*i*
alias:          pci:v00001002d00006766sv*sd*bc*sc*i*
alias:          pci:v00001002d00006765sv*sd*bc*sc*i*
alias:          pci:v00001002d00006764sv*sd*bc*sc*i*
alias:          pci:v00001002d00006763sv*sd*bc*sc*i*
alias:          pci:v00001002d00006762sv*sd*bc*sc*i*
alias:          pci:v00001002d00006761sv*sd*bc*sc*i*
alias:          pci:v00001002d00006760sv*sd*bc*sc*i*
alias:          pci:v00001002d0000675Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000675Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000675Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00006759sv*sd*bc*sc*i*
alias:          pci:v00001002d00006758sv*sd*bc*sc*i*
alias:          pci:v00001002d00006751sv*sd*bc*sc*i*
alias:          pci:v00001002d00006750sv*sd*bc*sc*i*
alias:          pci:v00001002d0000674Asv*sd*bc*sc*i*
alias:          pci:v00001002d00006749sv*sd*bc*sc*i*
alias:          pci:v00001002d00006748sv*sd*bc*sc*i*
alias:          pci:v00001002d00006747sv*sd*bc*sc*i*
alias:          pci:v00001002d00006746sv*sd*bc*sc*i*
alias:          pci:v00001002d00006745sv*sd*bc*sc*i*
alias:          pci:v00001002d00006744sv*sd*bc*sc*i*
alias:          pci:v00001002d00006743sv*sd*bc*sc*i*
alias:          pci:v00001002d00006742sv*sd*bc*sc*i*
alias:          pci:v00001002d00006741sv*sd*bc*sc*i*
alias:          pci:v00001002d00006740sv*sd*bc*sc*i*
alias:          pci:v00001002d0000673Esv*sd*bc*sc*i*
alias:          pci:v00001002d00006739sv*sd*bc*sc*i*
alias:          pci:v00001002d00006738sv*sd*bc*sc*i*
alias:          pci:v00001002d00006729sv*sd*bc*sc*i*
alias:          pci:v00001002d00006728sv*sd*bc*sc*i*
alias:          pci:v00001002d00006727sv*sd*bc*sc*i*
alias:          pci:v00001002d00006726sv*sd*bc*sc*i*
alias:          pci:v00001002d00006725sv*sd*bc*sc*i*
alias:          pci:v00001002d00006724sv*sd*bc*sc*i*
alias:          pci:v00001002d00006723sv*sd*bc*sc*i*
alias:          pci:v00001002d00006722sv*sd*bc*sc*i*
alias:          pci:v00001002d00006721sv*sd*bc*sc*i*
alias:          pci:v00001002d00006720sv*sd*bc*sc*i*
alias:          pci:v00001002d0000671Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000671Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000671Csv*sd*bc*sc*i*
alias:          pci:v00001002d00006719sv*sd*bc*sc*i*
alias:          pci:v00001002d00006718sv*sd*bc*sc*i*
alias:          pci:v00001002d00006709sv*sd*bc*sc*i*
alias:          pci:v00001002d00006708sv*sd*bc*sc*i*
alias:          pci:v00001002d00006707sv*sd*bc*sc*i*
alias:          pci:v00001002d00006706sv*sd*bc*sc*i*
alias:          pci:v00001002d00006705sv*sd*bc*sc*i*
alias:          pci:v00001002d00006704sv*sd*bc*sc*i*
alias:          pci:v00001002d00006703sv*sd*bc*sc*i*
alias:          pci:v00001002d00006702sv*sd*bc*sc*i*
alias:          pci:v00001002d00006701sv*sd*bc*sc*i*
alias:          pci:v00001002d00006700sv*sd*bc*sc*i*
alias:          pci:v00001002d00005E4Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00005E4Dsv*sd*bc*sc*i*
alias:          pci:v00001002d00005E4Csv*sd*bc*sc*i*
alias:          pci:v00001002d00005E4Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00005E4Asv*sd*bc*sc*i*
alias:          pci:v00001002d00005E48sv*sd*bc*sc*i*
alias:          pci:v00001002d00005D57sv*sd*bc*sc*i*
alias:          pci:v00001002d00005D52sv*sd*bc*sc*i*
alias:          pci:v00001002d00005D50sv*sd*bc*sc*i*
alias:          pci:v00001002d00005D4Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00005D4Esv*sd*bc*sc*i*
alias:          pci:v00001002d00005D4Dsv*sd*bc*sc*i*
alias:          pci:v00001002d00005D4Csv*sd*bc*sc*i*
alias:          pci:v00001002d00005D4Asv*sd*bc*sc*i*
alias:          pci:v00001002d00005D49sv*sd*bc*sc*i*
alias:          pci:v00001002d00005D48sv*sd*bc*sc*i*
alias:          pci:v00001002d00005C63sv*sd*bc*sc*i*
alias:          pci:v00001002d00005C61sv*sd*bc*sc*i*
alias:          pci:v00001002d00005B65sv*sd*bc*sc*i*
alias:          pci:v00001002d00005B64sv*sd*bc*sc*i*
alias:          pci:v00001002d00005B63sv*sd*bc*sc*i*
alias:          pci:v00001002d00005B62sv*sd*bc*sc*i*
alias:          pci:v00001002d00005B60sv*sd*bc*sc*i*
alias:          pci:v00001002d00005A62sv*sd*bc*sc*i*
alias:          pci:v00001002d00005A61sv*sd*bc*sc*i*
alias:          pci:v00001002d00005A42sv*sd*bc*sc*i*
alias:          pci:v00001002d00005A41sv*sd*bc*sc*i*
alias:          pci:v00001002d00005969sv*sd*bc*sc*i*
alias:          pci:v00001002d00005965sv*sd*bc*sc*i*
alias:          pci:v00001002d00005964sv*sd*bc*sc*i*
alias:          pci:v00001002d00005962sv*sd*bc*sc*i*
alias:          pci:v00001002d00005961sv*sd*bc*sc*i*
alias:          pci:v00001002d00005960sv*sd*bc*sc*i*
alias:          pci:v00001002d00005975sv*sd*bc*sc*i*
alias:          pci:v00001002d00005974sv*sd*bc*sc*i*
alias:          pci:v00001002d00005955sv*sd*bc*sc*i*
alias:          pci:v00001002d00005954sv*sd*bc*sc*i*
alias:          pci:v00001002d00005835sv*sd*bc*sc*i*
alias:          pci:v00001002d00005834sv*sd*bc*sc*i*
alias:          pci:v00001002d00005657sv*sd*bc*sc*i*
alias:          pci:v00001002d00005653sv*sd*bc*sc*i*
alias:          pci:v00001002d00005652sv*sd*bc*sc*i*
alias:          pci:v00001002d0000564Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000564Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000564Asv*sd*bc*sc*i*
alias:          pci:v00001002d00005554sv*sd*bc*sc*i*
alias:          pci:v00001002d00005552sv*sd*bc*sc*i*
alias:          pci:v00001002d00005551sv*sd*bc*sc*i*
alias:          pci:v00001002d00005550sv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Csv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000554Asv*sd*bc*sc*i*
alias:          pci:v00001002d00005549sv*sd*bc*sc*i*
alias:          pci:v00001002d00005548sv*sd*bc*sc*i*
alias:          pci:v00001002d00005464sv*sd*bc*sc*i*
alias:          pci:v00001002d00005462sv*sd*bc*sc*i*
alias:          pci:v00001002d00005460sv*sd*bc*sc*i*
alias:          pci:v00001002d0000515Esv*sd*bc*sc*i*
alias:          pci:v00001002d0000515Asv*sd*bc*sc*i*
alias:          pci:v00001002d00005159sv*sd*bc*sc*i*
alias:          pci:v00001002d00005158sv*sd*bc*sc*i*
alias:          pci:v00001002d00005157sv*sd*bc*sc*i*
alias:          pci:v00001002d0000514Dsv*sd*bc*sc*i*
alias:          pci:v00001002d0000514Csv*sd*bc*sc*i*
alias:          pci:v00001002d00005148sv*sd*bc*sc*i*
alias:          pci:v00001002d00005147sv*sd*bc*sc*i*
alias:          pci:v00001002d00005146sv*sd*bc*sc*i*
alias:          pci:v00001002d00005145sv*sd*bc*sc*i*
alias:          pci:v00001002d00005144sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E56sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E54sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E53sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E52sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E51sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E50sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E4Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004E4Asv*sd*bc*sc*i*
alias:          pci:v00001002d00004E49sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E48sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E47sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E46sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E45sv*sd*bc*sc*i*
alias:          pci:v00001002d00004E44sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C6Esv*sd*bc*sc*i*
alias:          pci:v00001002d00004C67sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C66sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C64sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C5Asv*sd*bc*sc*i*
alias:          pci:v00001002d00004C59sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C58sv*sd*bc*sc*i*
alias:          pci:v00001002d00004C57sv*sd*bc*sc*i*
alias:          pci:v00001002d00004B4Csv*sd*bc*sc*i*
alias:          pci:v00001002d00004B4Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004B4Asv*sd*bc*sc*i*
alias:          pci:v00001002d00004B49sv*sd*bc*sc*i*
alias:          pci:v00001002d00004B48sv*sd*bc*sc*i*
alias:          pci:v00001002d00004A54sv*sd*bc*sc*i*
alias:          pci:v00001002d00004A50sv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Esv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Dsv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Csv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004A4Asv*sd*bc*sc*i*
alias:          pci:v00001002d00004A49sv*sd*bc*sc*i*
alias:          pci:v00001002d00004A48sv*sd*bc*sc*i*
alias:          pci:v00001002d00004967sv*sd*bc*sc*i*
alias:          pci:v00001002d00004966sv*sd*bc*sc*i*
alias:          pci:v00001002d00004437sv*sd*bc*sc*i*
alias:          pci:v00001002d00004337sv*sd*bc*sc*i*
alias:          pci:v00001002d00004336sv*sd*bc*sc*i*
alias:          pci:v00001002d00004242sv*sd*bc*sc*i*
alias:          pci:v00001002d00004237sv*sd*bc*sc*i*
alias:          pci:v00001002d00004156sv*sd*bc*sc*i*
alias:          pci:v00001002d00004155sv*sd*bc*sc*i*
alias:          pci:v00001002d00004154sv*sd*bc*sc*i*
alias:          pci:v00001002d00004153sv*sd*bc*sc*i*
alias:          pci:v00001002d00004152sv*sd*bc*sc*i*
alias:          pci:v00001002d00004151sv*sd*bc*sc*i*
alias:          pci:v00001002d00004150sv*sd*bc*sc*i*
alias:          pci:v00001002d0000414Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000414Asv*sd*bc*sc*i*
alias:          pci:v00001002d00004149sv*sd*bc*sc*i*
alias:          pci:v00001002d00004148sv*sd*bc*sc*i*
alias:          pci:v00001002d00004147sv*sd*bc*sc*i*
alias:          pci:v00001002d00004146sv*sd*bc*sc*i*
alias:          pci:v00001002d00004145sv*sd*bc*sc*i*
alias:          pci:v00001002d00004144sv*sd*bc*sc*i*
alias:          pci:v00001002d00004137sv*sd*bc*sc*i*
alias:          pci:v00001002d00004136sv*sd*bc*sc*i*
alias:          pci:v00001002d00003E54sv*sd*bc*sc*i*
alias:          pci:v00001002d00003E50sv*sd*bc*sc*i*
alias:          pci:v00001002d00003155sv*sd*bc*sc*i*
alias:          pci:v00001002d00003154sv*sd*bc*sc*i*
alias:          pci:v00001002d00003152sv*sd*bc*sc*i*
alias:          pci:v00001002d00003151sv*sd*bc*sc*i*
alias:          pci:v00001002d00003150sv*sd*bc*sc*i*
depends:        drm,drm_kms_helper,ttm,i2c-algo-bit
intree:         Y
vermagic:       3.2.0-41-generic SMP mod_unload modversions 
parm:           no_wb:Disable AGP writeback for scratch registers (int)
parm:           modeset:Disable/Enable modesetting (int)
parm:           dynclks:Disable/Enable dynamic clocks (int)
parm:           r4xx_atom:Enable ATOMBIOS modesetting for R4xx (int)
parm:           vramlimit:Restrict VRAM for testing (int)
parm:           agpmode:AGP Mode (-1 == PCI) (int)
parm:           gartsize:Size of PCIE/IGP gart to setup in megabytes (32,64, etc)
 (int)
parm:           benchmark:Run benchmark (int)
parm:           test:Run tests (int)
parm:           connector_table:Force connector table (int)
parm:           tv:TV enable (0 = disable) (int)
parm:           audio:Audio enable (1 = enable) (int)
parm:           disp_priority:Display Priority (0 = auto, 1 = normal, 2 = high) (int)
parm:           hw_i2c:hw i2c engine enable (0 = disable) (int)
parm:           pcie_gen2:PCIE Gen2 mode (1 = enable) (int)
parm:           msi:MSI support (1 = enable, 0 = disable, -1 = auto) (int)
```

so i'm not sure what to do exactly, i need more information.

also if this by any means help, i get this message at login "Could not apply the stored configuration for monitors" in An alert dialog box, every time i log in except when i install fglrx with the radeon, and actuall in this case i can increase the resolution a little bit but cannot control the refresh rate, and of course no 3d.

---

### Post by arsenic23 on 2013-05-15
Have you tried to legacy drivers?  I know I had to switch over to them for my TV-PC with the last upgrade.

---

### Post by tgalati4 on 2013-05-15
If I understand correctly, you upgraded Ubuntu and the open driver gives you 3D, but not at high resolution.  You installed the proprietary driver (fglrx) and you get slightly higher resolution, but not the resolution and refresh rate that you had previously.  What was the previous version of Ubuntu that you were running?

It's possible that you have an old ATI configuration file that is messing up your display.  How did you perform the upgrade?  Was it a clean install or did you upgrade in place?

Searching "fglrx" in NewDocs brings up the following:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Have you tried some the techniques on these pages?

---

### Post by TheOne...more on 2013-05-15
sorry my bad, i didn't explain enough.

my previous ubuntu was gutsy, and it was working fine, but it was getting old and i decided to try something new. so i chose precise, and installed it on a new partition as a clean install. so it's not an upgrade in the sense you meant, and i didn't try upgrading this way cause i know how error prone process it is as you mentioned.

i tried the 9.3 ati .run driver, and it didn't load at startup. i was logged into terminal and had to issue startx command to use the graphical interface, so i didn't like it and uninstalled it. but the compiled .deb drivers are still on my hdd, and if there was some work around i can install them back.

also to give more detail, i have changed the xorg.conf file extension so that it doesn't conflict with detection process of the driver or the kernel. and there is no xorg.conf currently. also the xorg.conf file that i mentioned, was created by command

```
sudo X :1 -configure
```

i've skimmed through the ati and radeon howtos, but what they offered was actually all over the web, so it wasn't actually unfamiliar.

---

### Post by arsenic23 on 2013-05-15
I really think you need to be running fglrx-legacy with that card.  Yes, you do.  ATI dropped support for it so the normal fglrx driver will no longer work.  You need to get a fglrx-legacy ppa for your version of Ubuntu and install the driver from there.

---

### Post by TheOne...more on 2013-05-15
but i says that it supports 2xxx and 4xxx radeon hd cards, mine is rv350 9550 card. these are different chips.

---

### Post by arsenic23 on 2013-05-15
> **TheOne...more said:**
> but i says that it supports 2xxx and 4xxx radeon hd cards, mine is rv350 9550 card. these are different chips.

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/195535](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/195535)

---

### Post by TheOne...more on 2013-05-15
i guess i have no other option in the meantime, i'll try it and you'll hear from me in an hour or so.

---

### Post by TheOne...more on 2013-05-15
hi

i remove the radeon driver

```
sudo apt-get remove xserver-xorg-video-radeon xserver-xorg-video-ati radeontoll
```

i added the fglrx legacy ppa

```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
```

i restarted and installed

```
sudo apt-get install fglrx-legacy*
```

after it finished i restarted, and .... it booted to 800x600 screen, when i issued the command

```
sudo glxinfo
```

i got this

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_fog_distance, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_float, GL_ARB_texture_rectangle, 
    GL_ATI_texture_compression_3dc, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, GL_ARB_robustness, 
    GL_ARB_texture_storage

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ee 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ef 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fa 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x100 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x101 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x103 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x104 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x105 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x106 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x107 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x108 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x109 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x110 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x111 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x112 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x113 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x114 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x115 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x117 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x118 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x119 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x120 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x121 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x122 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x123 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x124 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x125 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x126 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x127 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x128 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x129 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x12a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x043 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x050 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x052 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x053 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x054 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x055 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x056 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x057 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x058 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x059 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x05a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x060 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x061 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x062 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x076  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x078  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x082  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x084  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x085  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x086  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x087  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x088  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x089  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x090 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x092 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x096 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x098 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x09e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ba  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0be  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0c8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ce  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow

```

the fglrx driver didn't even load, and i don't know whether it's me or the driver!

---

### Post by tgalati4 on 2013-05-15
I was under the impression that the fglrx-legacy video driver only worked with an older kernel than what is shipped with Precise.  Just because you can load a PPA doesn't mean that the software is compatible with your kernel.

From the askubuntu link:  

Radeon (Catalyst Legacy & Open Source)
ATI/AMD dropped Catalyst support for these cards in Catalyst 9-4. These cards are supported with the legacy ATI 9-3 Catalyst release, but you MUST use a kernel 2.6.28 (or earlier) and Xserver 1.5 (or earlier). For example, you can use Catalyst 9-3 if you're running Ubuntu 8.04 or Debian Lenny/5.0. Open source support is good and 3D is still improving.

So you might have to go back to an older version of Ubuntu with kernel 2.6.28 or use the open source (radeon) driver and be happy with the performance.  Not much of a choice.

---

### Post by TheOne...more on 2013-05-16
so what you mean is that there is no way that i can have i decent resolution with radeon driver at all, and there is no work around for that?

---

### Post by Yellow Pasque on 2013-05-16
Post your /var/log/Xorg.0.log

Note that glxgears is not a benchmark, and it will always give you 60fps since it uses vsync nowadays.

---

### Post by TheOne...more on 2013-05-16
to my surprise i found it's size 41.3MB, which part do you need? i'll try and grep it.

---

### Post by TheOne...more on 2013-05-16
i opened the xorg.0.log to see why it's so bloated, and i found after a little bit of analysis that that the file doesn't contain that much of information, the reason behind the bloating is an error message that is repeated continuously.

**the file starts like that:**


[    28.889] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.889] X Protocol Version 11, Revision 0
[    28.889] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    28.889] Current Operating System: Linux VaccumMachine 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64
[    28.889] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-41-generic root=UUID=689b565f-d75e-468e-a623-c0c4cab75568 ro quiet splash vt.handoff=7
[    28.889] Build Date: 11 April 2013  01:05:39PM
[    28.889] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.889] Current version of pixman: 0.24.4
[    28.889] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    28.889] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.890] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 16 08:48:17 2013
[    28.890] (++) Using config file: "/home/mainuser/xorg.conf.new"
[    28.890] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.890] (==) ServerLayout "X.org Configured"
[    28.890] (**) |-->Screen "Screen0" (0)
[    28.890] (**) |   |-->Monitor "Monitor0"
[    28.891] (**) |   |-->Device "Card0"
[    28.891] (**) |-->Screen "Screen1" (1)
[    28.891] (**) |   |-->Monitor "Monitor1"
[    28.891] (**) |   |-->Device "Card1"
[    28.891] (**) |-->Screen "Screen2" (2)
[    28.891] (**) |   |-->Monitor "Monitor2"
[    28.891] (**) |   |-->Device "Card2"
[    28.891] (**) |-->Input Device "Mouse0"
[    28.891] (**) |-->Input Device "Keyboard0"
[    28.891] (==) Automatically adding devices
[    28.891] (==) Automatically enabling devices
[    28.891] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.891] 	Entry deleted from font path.
[    28.891] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    28.891] 	Entry deleted from font path.
[    28.891] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.891] 	Entry deleted from font path.
[    28.891] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    28.891] 	Entry deleted from font path.
[    28.891] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    28.891] (**) ModulePath set to "/usr/lib/xorg/modules"
[    28.891] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    28.891] (WW) Disabling Mouse0
[    28.891] (WW) Disabling Keyboard0
[    28.891] (II) Loader magic: 0x7f02f3849b00
[    28.891] (II) Module ABI versions:
[    28.891] 	X.Org ANSI C Emulation: 0.4
[    28.891] 	X.Org Video Driver: 11.0
[    28.891] 	X.Org XInput driver : 16.0
[    28.891] 	X.Org Server Extension : 6.0
[    28.892] (--) PCI:*(0:1:0:0) 1002:4153:147b:6199 rev 0, Mem @ 0xe0000000/268435456, 0xff0f0000/65536, I/O @ 0x00009800/256, BIOS @ 0x????????/131072
[    28.892] (--) PCI: (0:1:0:1) 1002:4173:147b:6198 rev 0, Mem @ 0xd0000000/268435456, 0xff0e0000/65536
[    28.892] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.892] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    28.892] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    28.892] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    28.893] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    28.893] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    28.893] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    28.893] (II) LoadModule: "dbe"
[    28.893] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.893] (II) Module dbe: vendor="X.Org Foundation"
[    28.893] 	compiled for 1.11.3, module version = 1.0.0
[    28.893] 	Module class: X.Org Server Extension
[    28.893] 	ABI class: X.Org Server Extension, version 6.0
[    28.893] (II) Loading extension DOUBLE-BUFFER
[    28.893] (II) LoadModule: "dri"
[    28.893] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.893] (II) Module dri: vendor="X.Org Foundation"
[    28.893] 	compiled for 1.11.3, module version = 1.0.0
[    28.893] 	ABI class: X.Org Server Extension, version 6.0
[    28.894] (II) Loading extension XFree86-DRI
[    28.894] (II) LoadModule: "dri2"
[    28.894] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.894] (II) Module dri2: vendor="X.Org Foundation"
[    28.894] 	compiled for 1.11.3, module version = 1.2.0
[    28.894] 	ABI class: X.Org Server Extension, version 6.0
[    28.894] (II) Loading extension DRI2
[    28.894] (II) LoadModule: "extmod"
[    28.894] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.894] (II) Module extmod: vendor="X.Org Foundation"
[    28.894] 	compiled for 1.11.3, module version = 1.0.0
[    28.894] 	Module class: X.Org Server Extension
[    28.894] 	ABI class: X.Org Server Extension, version 6.0
[    28.894] (II) Loading extension MIT-SCREEN-SAVER
[    28.894] (II) Loading extension XFree86-VidModeExtension
[    28.894] (II) Loading extension XFree86-DGA
[    28.894] (II) Loading extension DPMS
[    28.894] (II) Loading extension XVideo
[    28.894] (II) Loading extension XVideo-MotionCompensation
[    28.894] (II) Loading extension X-Resource
[    28.894] (II) LoadModule: "glx"
[    28.894] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.894] (II) Module glx: vendor="X.Org Foundation"
[    28.894] 	compiled for 1.11.3, module version = 1.0.0
[    28.894] 	ABI class: X.Org Server Extension, version 6.0
[    28.894] (==) AIGLX enabled
[    28.894] (II) Loading extension GLX
[    28.894] (II) LoadModule: "record"
[    28.895] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.895] (II) Module record: vendor="X.Org Foundation"
[    28.895] 	compiled for 1.11.3, module version = 1.13.0
[    28.895] 	Module class: X.Org Server Extension
[    28.895] 	ABI class: X.Org Server Extension, version 6.0
[    28.895] (II) Loading extension RECORD
[    28.895] (II) LoadModule: "radeon"
[    28.918] (WW) Warning, couldn't open module radeon
[    28.918] (II) UnloadModule: "radeon"
[    28.918] (II) Unloading radeon
[    28.918] (EE) Failed to load module "radeon" (module does not exist, 0)
[    28.918] (II) LoadModule: "fbdev"
[    28.918] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.918] (II) Module fbdev: vendor="X.Org Foundation"
[    28.918] 	compiled for 1.11.3, module version = 0.4.2
[    28.919] 	ABI class: X.Org Video Driver, version 11.0
[    28.919] (II) LoadModule: "vesa"
[    28.919] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.919] (II) Module vesa: vendor="X.Org Foundation"
[    28.919] 	compiled for 1.11.3, module version = 2.3.0
[    28.919] 	Module class: X.Org Video Driver
[    28.919] 	ABI class: X.Org Video Driver, version 11.0
[    28.919] (==) Matched fglrx as autoconfigured driver 0
[    28.919] (==) Matched ati as autoconfigured driver 1
[    28.919] (==) Matched vesa as autoconfigured driver 2
[    28.919] (==) Matched fbdev as autoconfigured driver 3
[    28.919] (==) Assigned the driver to the xf86ConfigLayout
[    28.919] (II) LoadModule: "fglrx"
[    28.919] (WW) Warning, couldn't open module fglrx
[    28.919] (II) UnloadModule: "fglrx"
[    28.919] (II) Unloading fglrx
[    28.919] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.919] (II) LoadModule: "ati"
[    28.920] (WW) Warning, couldn't open module ati
[    28.920] (II) UnloadModule: "ati"
[    28.920] (II) Unloading ati
[    28.920] (EE) Failed to load module "ati" (module does not exist, 0)
[    28.920] (II) LoadModule: "vesa"
[    28.920] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.920] (II) Module vesa: vendor="X.Org Foundation"
[    28.920] 	compiled for 1.11.3, module version = 2.3.0
[    28.920] 	Module class: X.Org Video Driver
[    28.920] 	ABI class: X.Org Video Driver, version 11.0
[    28.920] (II) UnloadModule: "vesa"
[    28.920] (II) Unloading vesa
[    28.920] (II) Failed to load module "vesa" (already loaded, 0)
[    28.920] (II) LoadModule: "fbdev"
[    28.920] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.920] (II) Module fbdev: vendor="X.Org Foundation"
[    28.920] 	compiled for 1.11.3, module version = 0.4.2
[    28.920] 	ABI class: X.Org Video Driver, version 11.0
[    28.920] (II) UnloadModule: "fbdev"
[    28.920] (II) Unloading fbdev
[    28.920] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.920] (II) FBDEV: driver for framebuffer: fbdev
[    28.920] (II) VESA: driver for VESA chipsets: vesa
[    28.920] (++) using VT number 7

[    28.920] (II) Loading sub module "fbdevhw"
[    28.920] (II) LoadModule: "fbdevhw"
[    28.920] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.920] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.920] 	compiled for 1.11.3, module version = 0.0.2
[    28.920] 	ABI class: X.Org Video Driver, version 11.0
[    28.920] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.920] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.920] (**) FBDEV(0): claimed PCI slot 1@0:0:0
[    28.920] (II) FBDEV(0): using default device
[    28.920] (WW) Falling back to old probe method for vesa
[    28.921] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    28.921] (==) FBDEV(0): RGB weight 888
[    28.921] (==) FBDEV(0): Default visual is TrueColor
[    28.921] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.921] (II) FBDEV(0): hardware: radeondrmfb (video memory: 3072kB)
[    28.921] (II) FBDEV(0): checking modes against framebuffer device...
[    28.921] (II) FBDEV(0): checking modes against monitor...
[    28.921] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    28.921] (**) FBDEV(0):  Built-in mode "current"
[    28.921] (==) FBDEV(0): DPI set to (96, 96)
[    28.921] (II) Loading sub module "fb"
[    28.921] (II) LoadModule: "fb"
[    28.921] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.921] (II) Module fb: vendor="X.Org Foundation"
[    28.921] 	compiled for 1.11.3, module version = 1.0.0
[    28.921] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.921] (**) FBDEV(0): using shadow framebuffer
[    28.921] (II) Loading sub module "shadow"
[    28.921] (II) LoadModule: "shadow"
[    28.921] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    28.921] (II) Module shadow: vendor="X.Org Foundation"
[    28.921] 	compiled for 1.11.3, module version = 1.1.0
[    28.921] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.921] (II) UnloadModule: "vesa"
[    28.921] (II) Unloading vesa
[    28.921] (==) Depth 24 pixmap format is 32 bpp
[    28.922] (==) FBDEV(0): Backing store disabled

**then the error message appears from line 211 to 449 as:**


[    28.923] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

**to,**


[    28.925] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

**then the following lines go like that:**


[    28.925] (==) FBDEV(0): DPMS enabled
[    28.925] (==) RandR enabled
[    28.925] (II) Initializing built-in extension Generic Event Extension
[    28.925] (II) Initializing built-in extension SHAPE
[    28.925] (II) Initializing built-in extension MIT-SHM
[    28.925] (II) Initializing built-in extension XInputExtension
[    28.925] (II) Initializing built-in extension XTEST
[    28.925] (II) Initializing built-in extension BIG-REQUESTS
[    28.925] (II) Initializing built-in extension SYNC
[    28.925] (II) Initializing built-in extension XKEYBOARD
[    28.925] (II) Initializing built-in extension XC-MISC
[    28.925] (II) Initializing built-in extension SECURITY
[    28.925] (II) Initializing built-in extension XINERAMA
[    28.925] (II) Initializing built-in extension XFIXES
[    28.925] (II) Initializing built-in extension RENDER
[    28.925] (II) Initializing built-in extension RANDR
[    28.925] (II) Initializing built-in extension COMPOSITE
[    28.925] (II) Initializing built-in extension DAMAGE
[    28.934] (II) AIGLX: Screen 0 is not DRI2 capable
[    28.934] (II) AIGLX: Screen 0 is not DRI capable
[    28.957] (II) AIGLX: Loaded and initialized swrast
[    28.957] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    28.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.998] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.998] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.998] (II) LoadModule: "evdev"
[    28.998] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.999] (II) Module evdev: vendor="X.Org Foundation"
[    28.999] 	compiled for 1.11.3, module version = 2.7.0
[    28.999] 	Module class: X.Org XInput Driver
[    28.999] 	ABI class: X.Org XInput driver, version 16.0
[    28.999] (II) Using input driver 'evdev' for 'Power Button'
[    28.999] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.999] (**) Power Button: always reports core events
[    28.999] (**) evdev: Power Button: Device: "/dev/input/event1"
[    28.999] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.999] (--) evdev: Power Button: Found keys
[    28.999] (II) evdev: Power Button: Configuring as keyboard
[    28.999] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    28.999] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.999] (**) Option "xkb_rules" "evdev"
[    28.999] (**) Option "xkb_model" "pc105"
[    28.999] (**) Option "xkb_layout" "us"
[    29.000] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.000] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.000] (II) Using input driver 'evdev' for 'Power Button'
[    29.000] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.000] (**) Power Button: always reports core events
[    29.000] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.000] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.000] (--) evdev: Power Button: Found keys
[    29.000] (II) evdev: Power Button: Configuring as keyboard
[    29.000] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.000] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.000] (**) Option "xkb_rules" "evdev"
[    29.000] (**) Option "xkb_model" "pc105"
[    29.000] (**) Option "xkb_layout" "us"
[    29.001] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event2)
[    29.001] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.001] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.001] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.001] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.001] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event2"
[    29.001] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.001] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.001] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.001] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2/event2"
[    29.001] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 8)
[    29.001] (**) Option "xkb_rules" "evdev"
[    29.001] (**) Option "xkb_model" "pc105"
[    29.001] (**) Option "xkb_layout" "us"
[    29.002] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event3)
[    29.002] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev pointer catchall"
[    29.002] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.002] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.002] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.002] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.002] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event3"
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found 9 mouse buttons
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found scroll wheel(s)
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found relative axes
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y relative axes
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute axes
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute multitouch axes
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y absolute axes
[    29.002] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.002] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as mouse
[    29.002] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.002] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Adding scrollwheel support
[    29.002] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: YAxisMapping: buttons 4 and 5
[    29.002] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.002] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input3/event3"
[    29.002] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 9)
[    29.002] (**) Option "xkb_rules" "evdev"
[    29.002] (**) Option "xkb_model" "pc105"
[    29.002] (**) Option "xkb_layout" "us"
[    29.002] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: initialized for relative axes.
[    29.002] (WW) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: ignoring absolute axes.
[    29.003] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) keeping acceleration scheme 1
[    29.003] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration profile 0
[    29.003] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration factor: 2.000
[    29.003] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration threshold: 4
[    29.003] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/js0)
[    29.003] (II) No input driver specified, ignoring this device.
[    29.003] (II) This device may have been added with another device file.
[    29.003] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/mouse0)
[    29.003] (II) No input driver specified, ignoring this device.
[    29.003] (II) This device may have been added with another device file.
[    38.842] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.862] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.867] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.877] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.883] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.890] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.905] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.911] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.917] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.924] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.930] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.943] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.951] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.957] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.975] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.985] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    38.999] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.014] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.027] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm

**then the error message continues from line 579 to line 853808 at the end of the file like that:**


[  3415.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

**to,**


[ 17182.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

and this is all what is in the file i hope this is helpful.

---

### Post by Yellow Pasque on 2013-05-16
```
[ 28.920] (EE) Failed to load module "ati" (module does not exist, 0)
```
Did you remove the xserver-xorg-video-radeon package when you were screwing around with fglrx?

---

### Post by TheOne...more on 2013-05-16
yes, and i'm working without either at the moment. i'm waiting for some clear solution and i'm trying to work with as much nutral environment as possible to keep things simple.

---

### Post by TheOne...more on 2013-05-16
if you checked my previous posts you'll find that i removed these packages xserver-xorg-video-radeon xserver-xorg-video-ati radeontoll. also i removed the fglrx legacy that i downloaded and installed yesterday.

---

### Post by tgalati4 on 2013-05-16
I would reinstall the open source radeon driver and reboot then check your xorg.0.log file for errors.  You might be able to get higher resolution by creating a proper xorg.conf file with the correct modelines in it.  There are several tutorials on how to do that.  It's possible that the auto-detection is just using a failsafe resolution because it assumes that you will use the proprietary driver or it doesn't recognize your card correctly.  There may be some important details in log files.

For instance if you want 1600 x 1200 resolution at 85 Hertz you would use: *gtf 1600 1200 85*

tgalati4@Mint14-Extensa ~ $ gtf 1600 1200 85

  # 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
  Modeline "1600x1200_85.00"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync

Copy the Modeline into the correct location of your newly-created xorg.conf file, then reboot.

---

### Post by Yellow Pasque on 2013-05-16
> **tgalati4 said:**
> I would reinstall the open source radeon driver and reboot then check your xorg.0.log file for errors.
Yeah, that's what I had in mind. I wasn't aware that you removed the open-source driver because I skimmed through the part where you were spinning your wheels with fglrx.

Note: please use [ code ][ /code ] tages when posting large block of text

---

### Post by TheOne...more on 2013-05-16
the xorg.0.log that i previously posted was too long to be put in a single page, or even a complete thread, it was 800000 lines. i needed to clip much of it, and clarify what i showed, and what i removed, and why.

this is the new one. with xserver-xorg-video-ati and xserver-xorg-video-radeon packages installed.


```
[    29.447] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    29.447] X Protocol Version 11, Revision 0
[    29.447] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    29.447] Current Operating System: Linux VaccumMachine 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64
[    29.447] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-41-generic root=UUID=689b565f-d75e-468e-a623-c0c4cab75568 ro quiet splash vt.handoff=7
[    29.447] Build Date: 11 April 2013  01:05:39PM
[    29.447] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    29.447] Current version of pixman: 0.24.4
[    29.447] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    29.447] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.448] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 16 20:26:52 2013
[    29.448] (++) Using config file: "/home/mainuser/xorg.conf.new"
[    29.448] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.448] (==) ServerLayout "X.org Configured"
[    29.448] (**) |-->Screen "Screen0" (0)
[    29.448] (**) |   |-->Monitor "Monitor0"
[    29.449] (**) |   |-->Device "Card0"
[    29.449] (**) |-->Screen "Screen1" (1)
[    29.449] (**) |   |-->Monitor "Monitor1"
[    29.449] (**) |   |-->Device "Card1"
[    29.449] (**) |-->Input Device "Mouse0"
[    29.449] (**) |-->Input Device "Keyboard0"
[    29.449] (==) Automatically adding devices
[    29.449] (==) Automatically enabling devices
[    29.449] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.449] 	Entry deleted from font path.
[    29.449] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.449] 	Entry deleted from font path.
[    29.449] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.449] 	Entry deleted from font path.
[    29.449] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.449] 	Entry deleted from font path.
[    29.449] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    29.449] (**) ModulePath set to "/usr/lib/xorg/modules"
[    29.449] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    29.449] (WW) Disabling Mouse0
[    29.449] (WW) Disabling Keyboard0
[    29.449] (II) Loader magic: 0x7f0ee9b0bb00
[    29.449] (II) Module ABI versions:
[    29.449] 	X.Org ANSI C Emulation: 0.4
[    29.449] 	X.Org Video Driver: 11.0
[    29.449] 	X.Org XInput driver : 16.0
[    29.449] 	X.Org Server Extension : 6.0
[    29.450] (--) PCI:*(0:1:0:0) 1002:4153:147b:6199 rev 0, Mem @ 0xe0000000/268435456, 0xff0f0000/65536, I/O @ 0x00009800/256, BIOS @ 0x????????/131072
[    29.450] (--) PCI: (0:1:0:1) 1002:4173:147b:6198 rev 0, Mem @ 0xd0000000/268435456, 0xff0e0000/65536
[    29.450] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.450] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    29.450] (II) LoadModule: "dbe"
[    29.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.454] (II) Module dbe: vendor="X.Org Foundation"
[    29.454] 	compiled for 1.11.3, module version = 1.0.0
[    29.454] 	Module class: X.Org Server Extension
[    29.454] 	ABI class: X.Org Server Extension, version 6.0
[    29.454] (II) Loading extension DOUBLE-BUFFER
[    29.454] (II) LoadModule: "dri"
[    29.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.455] (II) Module dri: vendor="X.Org Foundation"
[    29.455] 	compiled for 1.11.3, module version = 1.0.0
[    29.455] 	ABI class: X.Org Server Extension, version 6.0
[    29.455] (II) Loading extension XFree86-DRI
[    29.455] (II) LoadModule: "dri2"
[    29.455] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.455] (II) Module dri2: vendor="X.Org Foundation"
[    29.455] 	compiled for 1.11.3, module version = 1.2.0
[    29.455] 	ABI class: X.Org Server Extension, version 6.0
[    29.455] (II) Loading extension DRI2
[    29.455] (II) LoadModule: "extmod"
[    29.455] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.455] (II) Module extmod: vendor="X.Org Foundation"
[    29.455] 	compiled for 1.11.3, module version = 1.0.0
[    29.455] 	Module class: X.Org Server Extension
[    29.455] 	ABI class: X.Org Server Extension, version 6.0
[    29.455] (II) Loading extension MIT-SCREEN-SAVER
[    29.455] (II) Loading extension XFree86-VidModeExtension
[    29.455] (II) Loading extension XFree86-DGA
[    29.455] (II) Loading extension DPMS
[    29.455] (II) Loading extension XVideo
[    29.455] (II) Loading extension XVideo-MotionCompensation
[    29.455] (II) Loading extension X-Resource
[    29.455] (II) LoadModule: "glx"
[    29.455] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.456] (II) Module glx: vendor="X.Org Foundation"
[    29.456] 	compiled for 1.11.3, module version = 1.0.0
[    29.456] 	ABI class: X.Org Server Extension, version 6.0
[    29.456] (==) AIGLX enabled
[    29.456] (II) Loading extension GLX
[    29.456] (II) LoadModule: "record"
[    29.456] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.456] (II) Module record: vendor="X.Org Foundation"
[    29.456] 	compiled for 1.11.3, module version = 1.13.0
[    29.456] 	Module class: X.Org Server Extension
[    29.456] 	ABI class: X.Org Server Extension, version 6.0
[    29.456] (II) Loading extension RECORD
[    29.456] (II) LoadModule: "fbdev"
[    29.456] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.456] (II) Module fbdev: vendor="X.Org Foundation"
[    29.456] 	compiled for 1.11.3, module version = 0.4.2
[    29.456] 	ABI class: X.Org Video Driver, version 11.0
[    29.456] (II) LoadModule: "vesa"
[    29.456] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.456] (II) Module vesa: vendor="X.Org Foundation"
[    29.456] 	compiled for 1.11.3, module version = 2.3.0
[    29.456] 	Module class: X.Org Video Driver
[    29.456] 	ABI class: X.Org Video Driver, version 11.0
[    29.456] (II) FBDEV: driver for framebuffer: fbdev
[    29.456] (II) VESA: driver for VESA chipsets: vesa
[    29.456] (++) using VT number 7

[    29.457] (II) Loading sub module "fbdevhw"
[    29.457] (II) LoadModule: "fbdevhw"
[    29.486] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.486] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.486] 	compiled for 1.11.3, module version = 0.0.2
[    29.486] 	ABI class: X.Org Video Driver, version 11.0
[    29.486] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.486] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.486] (**) FBDEV(0): claimed PCI slot 1@0:0:0
[    29.486] (II) FBDEV(0): using default device
[    29.486] (WW) Falling back to old probe method for vesa
[    29.486] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    29.486] (==) FBDEV(0): RGB weight 888
[    29.486] (==) FBDEV(0): Default visual is TrueColor
[    29.486] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.486] (II) FBDEV(0): hardware: radeondrmfb (video memory: 3072kB)
[    29.486] (II) FBDEV(0): checking modes against framebuffer device...
[    29.486] (II) FBDEV(0): checking modes against monitor...
[    29.486] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    29.486] (**) FBDEV(0):  Built-in mode "current"
[    29.486] (==) FBDEV(0): DPI set to (96, 96)
[    29.486] (II) Loading sub module "fb"
[    29.486] (II) LoadModule: "fb"
[    29.487] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.487] (II) Module fb: vendor="X.Org Foundation"
[    29.487] 	compiled for 1.11.3, module version = 1.0.0
[    29.487] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.487] (**) FBDEV(0): using shadow framebuffer
[    29.487] (II) Loading sub module "shadow"
[    29.487] (II) LoadModule: "shadow"
[    29.487] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.487] (II) Module shadow: vendor="X.Org Foundation"
[    29.487] 	compiled for 1.11.3, module version = 1.1.0
[    29.487] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.487] (II) UnloadModule: "vesa"
[    29.487] (II) Unloading vesa
[    29.487] (==) Depth 24 pixmap format is 32 bpp
[    29.488] (==) FBDEV(0): Backing store disabled
[    29.488] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.488] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.488] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.488] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.489] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.490] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.491] (==) FBDEV(0): DPMS enabled
[    29.491] (==) RandR enabled
[    29.491] (II) Initializing built-in extension Generic Event Extension
[    29.491] (II) Initializing built-in extension SHAPE
[    29.491] (II) Initializing built-in extension MIT-SHM
[    29.491] (II) Initializing built-in extension XInputExtension
[    29.491] (II) Initializing built-in extension XTEST
[    29.491] (II) Initializing built-in extension BIG-REQUESTS
[    29.491] (II) Initializing built-in extension SYNC
[    29.491] (II) Initializing built-in extension XKEYBOARD
[    29.491] (II) Initializing built-in extension XC-MISC
[    29.491] (II) Initializing built-in extension SECURITY
[    29.491] (II) Initializing built-in extension XINERAMA
[    29.491] (II) Initializing built-in extension XFIXES
[    29.491] (II) Initializing built-in extension RENDER
[    29.491] (II) Initializing built-in extension RANDR
[    29.491] (II) Initializing built-in extension COMPOSITE
[    29.491] (II) Initializing built-in extension DAMAGE
[    29.500] (II) AIGLX: Screen 0 is not DRI2 capable
[    29.500] (II) AIGLX: Screen 0 is not DRI capable
[    29.522] (II) AIGLX: Loaded and initialized swrast
[    29.522] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    29.561] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.565] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.565] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.565] (II) LoadModule: "evdev"
[    29.565] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.565] (II) Module evdev: vendor="X.Org Foundation"
[    29.565] 	compiled for 1.11.3, module version = 2.7.0
[    29.565] 	Module class: X.Org XInput Driver
[    29.565] 	ABI class: X.Org XInput driver, version 16.0
[    29.565] (II) Using input driver 'evdev' for 'Power Button'
[    29.565] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.565] (**) Power Button: always reports core events
[    29.565] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.565] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.565] (--) evdev: Power Button: Found keys
[    29.565] (II) evdev: Power Button: Configuring as keyboard
[    29.566] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.566] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.566] (**) Option "xkb_rules" "evdev"
[    29.566] (**) Option "xkb_model" "pc105"
[    29.566] (**) Option "xkb_layout" "us"
[    29.566] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.566] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.566] (II) Using input driver 'evdev' for 'Power Button'
[    29.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.566] (**) Power Button: always reports core events
[    29.566] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.566] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.566] (--) evdev: Power Button: Found keys
[    29.566] (II) evdev: Power Button: Configuring as keyboard
[    29.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.567] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.567] (**) Option "xkb_rules" "evdev"
[    29.567] (**) Option "xkb_model" "pc105"
[    29.567] (**) Option "xkb_layout" "us"
[    29.567] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event2)
[    29.567] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.567] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.567] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.567] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event2"
[    29.567] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.567] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.567] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.567] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2/event2"
[    29.568] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 8)
[    29.568] (**) Option "xkb_rules" "evdev"
[    29.568] (**) Option "xkb_model" "pc105"
[    29.568] (**) Option "xkb_layout" "us"
[    29.568] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event3)
[    29.568] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev pointer catchall"
[    29.568] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.568] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.568] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.568] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.568] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event3"
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found 9 mouse buttons
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found scroll wheel(s)
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found relative axes
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y relative axes
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute axes
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute multitouch axes
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y absolute axes
[    29.569] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.569] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as mouse
[    29.569] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.569] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Adding scrollwheel support
[    29.569] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: YAxisMapping: buttons 4 and 5
[    29.569] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.569] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input3/event3"
[    29.569] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 9)
[    29.569] (**) Option "xkb_rules" "evdev"
[    29.569] (**) Option "xkb_model" "pc105"
[    29.569] (**) Option "xkb_layout" "us"
[    29.569] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: initialized for relative axes.
[    29.569] (WW) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: ignoring absolute axes.
[    29.569] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) keeping acceleration scheme 1
[    29.569] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration profile 0
[    29.569] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration factor: 2.000
[    29.569] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration threshold: 4
[    29.570] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/js0)
[    29.570] (II) No input driver specified, ignoring this device.
[    29.570] (II) This device may have been added with another device file.
[    29.570] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/mouse0)
[    29.570] (II) No input driver specified, ignoring this device.
[    29.570] (II) This device may have been added with another device file.
[    37.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.454] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.470] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.479] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.485] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.491] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.495] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.500] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.518] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.523] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.533] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.545] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.550] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.556] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    37.562] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
```

isn't there any way to patch catalyst 9.3 to work with x11r7.7, or is it possible to down-date/degrade the x11 that i have to 7.4 on precise?

---

### Post by Yellow Pasque on 2013-05-16
> **TheOne...more said:**
> isn't there any way to patch catalyst 9.3 to work with x11r7.7, or is it possible to down-date/degrade the x11 that i have to 7.4 on precise?

No. Just forget about fglrx/Catalyst. It's not going to work on modern distros.

Okay, so xorg is using fbdev. Weird. What happens when you use this for /etc/X11/xorg.conf?
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "radeon"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier       "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by TheOne...more on 2013-05-16
the x :1 -configure command creates xorg.conf file with two "screen" sections and two "device" sections and two "monitor" sections. where do i place the lines you posted?

---

### Post by TheOne...more on 2013-05-16
here is the file

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card0"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card1"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Yellow Pasque on 2013-05-16
Just delete everything that already exists and use the xorg.conf I gave you. Then, we'll look at the log and hopefully see what happens when radeon tries to load

---

### Post by TheOne...more on 2013-05-16
here is the new log

```
[    29.097] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    29.097] X Protocol Version 11, Revision 0
[    29.097] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    29.097] Current Operating System: Linux VaccumMachine 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64
[    29.097] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-41-generic root=UUID=689b565f-d75e-468e-a623-c0c4cab75568 ro quiet splash vt.handoff=7
[    29.097] Build Date: 11 April 2013  01:05:39PM
[    29.097] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    29.097] Current version of pixman: 0.24.4
[    29.097] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    29.097] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.097] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 16 21:15:35 2013
[    29.097] (++) Using config file: "/home/mainuser/xorg.conf.new"
[    29.097] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.098] (==) ServerLayout "X.org Configured"
[    29.098] (**) |-->Screen "Screen0" (0)
[    29.098] (**) |   |-->Monitor "Monitor0"
[    29.098] (**) |   |-->Device "Card0"
[    29.098] (**) |-->Screen "Screen1" (1)
[    29.098] (**) |   |-->Monitor "Monitor1"
[    29.098] (**) |   |-->Device "Card1"
[    29.098] (**) |-->Input Device "Mouse0"
[    29.098] (**) |-->Input Device "Keyboard0"
[    29.098] (==) Automatically adding devices
[    29.098] (==) Automatically enabling devices
[    29.098] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.098] 	Entry deleted from font path.
[    29.098] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.098] 	Entry deleted from font path.
[    29.098] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.098] 	Entry deleted from font path.
[    29.098] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.098] 	Entry deleted from font path.
[    29.098] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    29.098] (**) ModulePath set to "/usr/lib/xorg/modules"
[    29.098] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    29.099] (WW) Disabling Mouse0
[    29.099] (WW) Disabling Keyboard0
[    29.099] (II) Loader magic: 0x7ffbb94f6b00
[    29.099] (II) Module ABI versions:
[    29.099] 	X.Org ANSI C Emulation: 0.4
[    29.099] 	X.Org Video Driver: 11.0
[    29.099] 	X.Org XInput driver : 16.0
[    29.099] 	X.Org Server Extension : 6.0
[    29.099] (--) PCI:*(0:1:0:0) 1002:4153:147b:6199 rev 0, Mem @ 0xe0000000/268435456, 0xff0f0000/65536, I/O @ 0x00009800/256, BIOS @ 0x????????/131072
[    29.099] (--) PCI: (0:1:0:1) 1002:4173:147b:6198 rev 0, Mem @ 0xd0000000/268435456, 0xff0e0000/65536
[    29.100] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.100] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    29.100] (II) LoadModule: "dbe"
[    29.105] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.105] (II) Module dbe: vendor="X.Org Foundation"
[    29.105] 	compiled for 1.11.3, module version = 1.0.0
[    29.105] 	Module class: X.Org Server Extension
[    29.105] 	ABI class: X.Org Server Extension, version 6.0
[    29.105] (II) Loading extension DOUBLE-BUFFER
[    29.105] (II) LoadModule: "dri"
[    29.105] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.106] (II) Module dri: vendor="X.Org Foundation"
[    29.106] 	compiled for 1.11.3, module version = 1.0.0
[    29.106] 	ABI class: X.Org Server Extension, version 6.0
[    29.106] (II) Loading extension XFree86-DRI
[    29.106] (II) LoadModule: "dri2"
[    29.106] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.106] (II) Module dri2: vendor="X.Org Foundation"
[    29.106] 	compiled for 1.11.3, module version = 1.2.0
[    29.106] 	ABI class: X.Org Server Extension, version 6.0
[    29.106] (II) Loading extension DRI2
[    29.106] (II) LoadModule: "extmod"
[    29.106] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.106] (II) Module extmod: vendor="X.Org Foundation"
[    29.106] 	compiled for 1.11.3, module version = 1.0.0
[    29.106] 	Module class: X.Org Server Extension
[    29.106] 	ABI class: X.Org Server Extension, version 6.0
[    29.106] (II) Loading extension MIT-SCREEN-SAVER
[    29.106] (II) Loading extension XFree86-VidModeExtension
[    29.106] (II) Loading extension XFree86-DGA
[    29.106] (II) Loading extension DPMS
[    29.106] (II) Loading extension XVideo
[    29.106] (II) Loading extension XVideo-MotionCompensation
[    29.106] (II) Loading extension X-Resource
[    29.106] (II) LoadModule: "glx"
[    29.106] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.106] (II) Module glx: vendor="X.Org Foundation"
[    29.107] 	compiled for 1.11.3, module version = 1.0.0
[    29.107] 	ABI class: X.Org Server Extension, version 6.0
[    29.107] (==) AIGLX enabled
[    29.107] (II) Loading extension GLX
[    29.107] (II) LoadModule: "record"
[    29.107] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.107] (II) Module record: vendor="X.Org Foundation"
[    29.107] 	compiled for 1.11.3, module version = 1.13.0
[    29.107] 	Module class: X.Org Server Extension
[    29.107] 	ABI class: X.Org Server Extension, version 6.0
[    29.107] (II) Loading extension RECORD
[    29.107] (II) LoadModule: "fbdev"
[    29.107] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.107] (II) Module fbdev: vendor="X.Org Foundation"
[    29.107] 	compiled for 1.11.3, module version = 0.4.2
[    29.107] 	ABI class: X.Org Video Driver, version 11.0
[    29.107] (II) LoadModule: "vesa"
[    29.107] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.107] (II) Module vesa: vendor="X.Org Foundation"
[    29.107] 	compiled for 1.11.3, module version = 2.3.0
[    29.107] 	Module class: X.Org Video Driver
[    29.107] 	ABI class: X.Org Video Driver, version 11.0
[    29.107] (II) FBDEV: driver for framebuffer: fbdev
[    29.107] (II) VESA: driver for VESA chipsets: vesa
[    29.107] (++) using VT number 7

[    29.107] (II) Loading sub module "fbdevhw"
[    29.107] (II) LoadModule: "fbdevhw"
[    29.137] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.137] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.137] 	compiled for 1.11.3, module version = 0.0.2
[    29.137] 	ABI class: X.Org Video Driver, version 11.0
[    29.137] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.137] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.137] (**) FBDEV(0): claimed PCI slot 1@0:0:0
[    29.137] (II) FBDEV(0): using default device
[    29.137] (WW) Falling back to old probe method for vesa
[    29.137] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    29.137] (==) FBDEV(0): RGB weight 888
[    29.137] (==) FBDEV(0): Default visual is TrueColor
[    29.137] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.137] (II) FBDEV(0): hardware: radeondrmfb (video memory: 3072kB)
[    29.137] (II) FBDEV(0): checking modes against framebuffer device...
[    29.137] (II) FBDEV(0): checking modes against monitor...
[    29.137] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    29.137] (**) FBDEV(0):  Built-in mode "current"
[    29.137] (==) FBDEV(0): DPI set to (96, 96)
[    29.137] (II) Loading sub module "fb"
[    29.137] (II) LoadModule: "fb"
[    29.137] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.138] (II) Module fb: vendor="X.Org Foundation"
[    29.138] 	compiled for 1.11.3, module version = 1.0.0
[    29.138] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.138] (**) FBDEV(0): using shadow framebuffer
[    29.138] (II) Loading sub module "shadow"
[    29.138] (II) LoadModule: "shadow"
[    29.138] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.138] (II) Module shadow: vendor="X.Org Foundation"
[    29.138] 	compiled for 1.11.3, module version = 1.1.0
[    29.138] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.138] (II) UnloadModule: "vesa"
[    29.138] (II) Unloading vesa
[    29.138] (==) Depth 24 pixmap format is 32 bpp
[    29.139] (==) FBDEV(0): Backing store disabled
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.139] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.140] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.141] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    29.142] (==) FBDEV(0): DPMS enabled
[    29.142] (==) RandR enabled
[    29.142] (II) Initializing built-in extension Generic Event Extension
[    29.142] (II) Initializing built-in extension SHAPE
[    29.142] (II) Initializing built-in extension MIT-SHM
[    29.142] (II) Initializing built-in extension XInputExtension
[    29.142] (II) Initializing built-in extension XTEST
[    29.142] (II) Initializing built-in extension BIG-REQUESTS
[    29.142] (II) Initializing built-in extension SYNC
[    29.142] (II) Initializing built-in extension XKEYBOARD
[    29.142] (II) Initializing built-in extension XC-MISC
[    29.142] (II) Initializing built-in extension SECURITY
[    29.142] (II) Initializing built-in extension XINERAMA
[    29.142] (II) Initializing built-in extension XFIXES
[    29.142] (II) Initializing built-in extension RENDER
[    29.142] (II) Initializing built-in extension RANDR
[    29.142] (II) Initializing built-in extension COMPOSITE
[    29.142] (II) Initializing built-in extension DAMAGE
[    29.151] (II) AIGLX: Screen 0 is not DRI2 capable
[    29.151] (II) AIGLX: Screen 0 is not DRI capable
[    29.174] (II) AIGLX: Loaded and initialized swrast
[    29.174] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    29.212] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.216] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.216] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.216] (II) LoadModule: "evdev"
[    29.216] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.217] (II) Module evdev: vendor="X.Org Foundation"
[    29.217] 	compiled for 1.11.3, module version = 2.7.0
[    29.217] 	Module class: X.Org XInput Driver
[    29.217] 	ABI class: X.Org XInput driver, version 16.0
[    29.217] (II) Using input driver 'evdev' for 'Power Button'
[    29.217] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.217] (**) Power Button: always reports core events
[    29.217] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.217] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.217] (--) evdev: Power Button: Found keys
[    29.217] (II) evdev: Power Button: Configuring as keyboard
[    29.217] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.217] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.217] (**) Option "xkb_rules" "evdev"
[    29.217] (**) Option "xkb_model" "pc105"
[    29.217] (**) Option "xkb_layout" "us"
[    29.218] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.218] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.218] (II) Using input driver 'evdev' for 'Power Button'
[    29.218] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.218] (**) Power Button: always reports core events
[    29.218] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.218] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.218] (--) evdev: Power Button: Found keys
[    29.218] (II) evdev: Power Button: Configuring as keyboard
[    29.218] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.218] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.218] (**) Option "xkb_rules" "evdev"
[    29.218] (**) Option "xkb_model" "pc105"
[    29.218] (**) Option "xkb_layout" "us"
[    29.219] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event2)
[    29.219] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.219] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.219] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.219] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.219] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event2"
[    29.219] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.219] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.219] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.219] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2/event2"
[    29.219] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 8)
[    29.219] (**) Option "xkb_rules" "evdev"
[    29.219] (**) Option "xkb_model" "pc105"
[    29.219] (**) Option "xkb_layout" "us"
[    29.220] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event3)
[    29.220] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev pointer catchall"
[    29.220] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    29.220] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    29.220] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.220] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    29.220] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event3"
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found 9 mouse buttons
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found scroll wheel(s)
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found relative axes
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y relative axes
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute axes
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute multitouch axes
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y absolute axes
[    29.220] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    29.220] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as mouse
[    29.220] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    29.220] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Adding scrollwheel support
[    29.220] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: YAxisMapping: buttons 4 and 5
[    29.220] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input3/event3"
[    29.220] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 9)
[    29.220] (**) Option "xkb_rules" "evdev"
[    29.220] (**) Option "xkb_model" "pc105"
[    29.220] (**) Option "xkb_layout" "us"
[    29.220] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: initialized for relative axes.
[    29.220] (WW) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: ignoring absolute axes.
[    29.221] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) keeping acceleration scheme 1
[    29.221] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration profile 0
[    29.221] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration factor: 2.000
[    29.221] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration threshold: 4
[    29.221] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/js0)
[    29.221] (II) No input driver specified, ignoring this device.
[    29.221] (II) This device may have been added with another device file.
[    29.221] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/mouse0)
[    29.222] (II) No input driver specified, ignoring this device.
[    29.222] (II) This device may have been added with another device file.
[    39.522] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.540] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.548] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.559] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.575] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.580] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.589] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.598] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.619] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.647] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.655] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.662] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.683] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
[    39.699] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A63FD07FDF2DBA0B722C72C4A51D0EB3D10AE42.xkm
```

---

### Post by TheOne...more on 2013-05-17
i think i'll retract to windows for the moment, until i find a woking linux or unix distro. i think windows is gaining over linux at the moment.

---

### Post by Mark Phelps on 2013-05-17
Understand ... it can be very difficult to get older ATI cards working well in Linux, what with AMD repeatedly dropping support for their cards over the years.

When you go back to Windows, understand that the most current drivers for your card are Catalyst 10.2 -- Vista drivers.  They might work in Win7, but you may have to install them using Vista compatibility mode.

---

### Post by tgalati4 on 2013-05-17
Your system is definitely messed up.  Do you have two monitors hooked up?  If so, remove one.  Also, it appears that xorg is using a different configuration file:

[    29.097] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 16 21:15:35 2013
[    29.097] (++) Using config file: "**/home/mainuser/xorg.conf.new**"
[    29.097] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

And the *radeon* driver is not loading and the framebuffer (fbdev) and VESA driver are being loaded instead.  As a result, the framebuffer on the ATI card is giving errors probably because it does not conform to a standard framebuffer device.  Thus, you only get a low (VESA) resolution with no 3D capability.  Somehow removing the open drivers and installing the proprietary drivers has left your system in an indeterminate state.  One that does not behave the way we would expect.

If you delete the offending xorg.conf.new file and use the file in post #23 and locate it in /etc/X11/xorg.conf, you should be able to get your card to work.  If you can't get to a specific resolution, then use the *gtf* command to get the correct modeline.

Be sure to disconnect any additional monitors.  We want only one monitor defined.

---

### Post by Portaro on 2013-05-17
I have a big problems of less graphic performance in the initial Ubuntu/Xubuntu releases on past, i do some steps like the steps refered on the preview posts like make new xorg.

I solve my problem of bad 3d performance with the installation of mesa-utils (i think this package is necessary for ATI) without this the pc freezes constantly on desktops and laptops i have this problem on my two pcs with ati cards and in the last releases the same problem exists also, i experiment Lubuntu 13.04 and xubuntu 13.04 and the pcs freezes like in past, so for new users with ati maybe is important refere that mesa-utils can be the solution for the freezing and bad aceleration graphic performance in Ubuntus, all you need is install mesa-uitls on synaptic and the problem disappear.

---

