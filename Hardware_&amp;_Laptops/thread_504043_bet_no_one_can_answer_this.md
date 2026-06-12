---
title: "bet no one can answer this"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by kingofleo on 2007-07-18
In the MadWiFi v.0.9.2 source code it appears that the function ath_calibrate() is called periodically. This function calls ath_hal_getrfgain() and if it returns HAL_RFGAIN_NEED_CHANGE, the function ath_reset() is called. AL_RFGAIN_NEED_CHANGE may mean that new gain values must be loaded, but ath_reset() does many other things including dropping any enqueued frames. As we don't have a datasheet for PHY chip of Atheros PHY (5112), we are not sure but it seems it refers to ath_hal_getrfgain() (as defined in openHAL sources). Could you explain ath_hal_getrfgain() functionality of current HAL(not openHAL), and why does it need a full device reset?:popcorn:
mail me at [email]nikvoodoo@gmail.com[/email] the address where u hve done this problem:guitar:

---

### Post by Death_Sargent on 2007-07-19
troll on. it doesn't

---

