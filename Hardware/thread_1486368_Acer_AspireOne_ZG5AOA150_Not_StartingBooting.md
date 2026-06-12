---
title: "Acer AspireOne ZG5/AOA150 Not Starting/Booting"
date: 2010-05-17
forum: Hardware
---

### Post by grumpy.medic on 2010-05-17
**Issue:** Acer AspireOne ZG5/AOA150 Not Starting/Booting.

**Background:** One day, after doing nothing intrusive what-so-ever to my AspireOne, it would not longer boot. All I could see was the batter-indicator light as well as the power-button light and that was it. The LCD would not even power on anymore. After 3 hours or researching and trying, I found the solution. I will be sharing my Eureka moments with you below.

**Symptoms:** System no longer boots. Screen does not power on anymore. HDD does not spin up (if equipped with non-SSD). Only lights are battery indicator/power-button light.

**How-to:** Don't worry. Your system is not bricked yet. This means, that somehow, some way the BIOS files got corrupted. Luckily enough, the ZG is equipped with a BIOS restore feature that does not require the system to boot/fully power up.

You need:

[LIST]
[*]USB flash drive (at least 16MB)

[*][Latest BIOS files/updates from ACER]("http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_3310_A_AOA110%20&%20AOA150.zip?acerid=633850493862245097&Step1=Netbook&Step2=Aspire%20One&Step3=AOA150&OS=X01&LC=en&BC=Acer&SC=PA_7") 

[*]Another working system
[/LIST]

After you have gathered these items, go to your second system and extract the zip file containing our BIOS files. Navigate to [COLOR="Blue"]*~\BIOS_Acer_3310_A_AOA110 & AOA150\BIOS_ACER_3310_Windows_AOA110 & AOA150\Dos_Flash*[/COLOR]. Now copy the following files onto the USB-flash drive ([COLOR="Red"]make sure that it has been formatted for FAT-32 and is empty of any other files![/COLOR]):

[LIST]
[*][COLOR="blue"]FLASHIT.EXE[/COLOR]

[*][COLOR="blue"]3310.fd[/COLOR]
[/LIST]

After they are copied over the the USB-flash drive, rename [COLOR="blue"]*3310.fd*[/COLOR] to [COLOR="Blue"]*ZG5IA32.fd*[/COLOR].

Now, you are ready for magic time! Make sure you netbook is plugged into the charger/outlet and is powered off (green light on power button should be dark). Plug in your USB-flash drive, and hold the following keys for about 5-7 seconds:

Fn and Esc while pressing the power button.

Keep holding these two keys and release agter 5-7 seconds, if you did it right, the green power light will be flashing and you will see the light on our USB-flash drive flicker (if equipped). The process can take between 2-7 minutes, [COLOR="Red"]**DO NOT PRESS ANY KEYS AFTER THE POWER-BUTTON STARTS FLASHING -- LET IT SIT!**[/COLOR] If everything went well, it will automatically reboot and start up like it should.

If it does not work right away, keep trying, it took me 3 trys to get it right.

Also, [COLOR="red"]**make sure that you have the AOA110/150 model, this will brick any other system!**[/COLOR]

If my write up is too convoluted for you, [here]("http://netbooks-us.custhelp.com/app/answers/detail/a_id/66/session/L3NpZC9jZDhmaDgqag%3D%3D/sno/0") is the article I found at Acer 'after' I worked it out myself.

Why did I post this? I could NOT find a decent write up on it anywhere, and there is lots of ZG5 users out there... just sharing the love!

~
Cheers

---

