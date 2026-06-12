---
title: "Driver for ATI Mobility Radeon(TM) HD 4650"
date: 2013-06-14
forum: Hardware
---

### Post by Jose Ponteira on 2013-06-14
How can I instal the driver for my graphics card [COLOR=#a9a9a9]ATI Mobility Radeon (TM) HD 4650 supporting HyperMemory technology ([/COLOR][COLOR=#a9a9a9]MT)[/COLOR].
I thank you in advance to all who try to help me

---

### Post by QIII on 2013-06-14
Hello!

The answer to your question depends on which version of Ubuntu you are using.  Could you let us know what that is?

Thanks.

---

### Post by Jose Ponteira on 2013-06-14
I have instaled ubuntu 13.04 32 bits

---

### Post by Cheesemill on 2013-06-14
You are already using the only driver available for your graphics card, this is the open source radeon driver that comes built into Ubuntu.

ATI dropped support for all of the 2/4xxx series cards last summer so they don't write the closed source drivers for them any more.

---

### Post by QIII on 2013-06-14
I'm sure that is unhappy news for you.

Although there is a legacy driver, it will not work with Ubuntu versions 12.04.2 and beyond because of changes to the kernel and X Server.

There are methods by which your system can be hacked to function, but I so strongly recommend against them that I won't even point you to them.  They basically break your installation.  I've had to help two people sort things out already.

If you want to, you can continue to use the open source Radeon driver Ubuntu is using right now.  For the vast majority of people it will work just fine.

If you really must have the proprietary ATI driver, you will need to fall back to 12.04.1 or earlier.  Then I would suggest using the proprietary driver in the Precise repo -- but not the fglrx-updates version.

There is really nothing to be done about this.  Neither anyone at Canonical nor any open source developer do anything to change this.  The proprietary ATI driver is not open source and can't be modified.  This will not change with newer versions of Ubuntu or any updates from the repos.

12.04 and 12.04.1 are supported until 2017.  That means you can enjoy Ubuntu for another four years without the expense of a new card and still use the proprietary driver.  Or just continue as you are doing.

Sorry for the bad news, but that is simply the way it is.

Best wishes.

---

### Post by Jose Ponteira on 2013-06-14
Thankyou. the information You give is very useful. I think i hav to stay like i am now.

---

