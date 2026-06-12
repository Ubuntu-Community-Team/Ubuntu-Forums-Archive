---
title: "Laptop Battery Voltages"
date: 2023-07-06
forum: Hardware
---

### Post by Geoff_Lane on 2023-07-06
Appreciate most electrical items have voltage regulators nowadays but I just bought a replacement battery for my ageing Toshiba Satellite laptop. 

The original battery shows 14.4V - the replacements all appear to be 14.8V (Checked a number of sites).

The replacement shows 14.8V marked on the case but when fully charged the battery monitor says 16.1V obviously dropping off as charge diminishes.

As I cannot recall what the original battery used to show has anyone any opinions as to why the battery should be labelled 14.8V but record more when charged, and more to the point, is this an issue for the computer?

Geoff

---

### Post by #&amp;thj^% on 2023-07-06
Hpefully your not>> "Can I use a battery which has a different voltage rating than my original battery?
No, the voltage rating has to match that of the original battery or as recommended by the computer manual. Using a battery with a different voltage setting can damage the laptop."
That's the rule of thumb I follow in replacements.

Now a higher milliamp (mAh)
Is Ok ,  Higher mAh ratings indicate that your battery will last longer. Although the milliamps may be higher, the voltage will always remain the same. If you have received a laptop battery that has a completely different voltage than your original laptop battery, please contact  your supplier again.

But I'm not sure 16.1V is a good thing at all, that just sets my spider senses off.
Can you provide us with the output of this please:
```
upower -e
/org/freedesktop/UPower/devices/line_power_ADP0
/org/freedesktop/UPower/devices/battery_BAT0
/org/freedesktop/UPower/devices/DisplayDevice
```
Will show my battery ie:"BAT0"
Now more info
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Celxpert
  model:                L19C4PC0
  serial:               1532
  power supply:         yes
  updated:              Thu 06 Jul 2023 10:49:04 AM MDT (26 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              55.07 Wh
    energy-empty:        0 Wh
    energy-full:         55.07 Wh
    energy-full-design:  60 Wh
    energy-rate:         0.051 W
    voltage:             17.294 V
    charge-cycles:       33
    percentage:          100%
    capacity:            91.3667%
    technology:          lithium-polymer
    icon-name:          'battery-full-charged-symbolic'


```

---

### Post by Geoff_Lane on 2023-07-06
Thanks for very prompt reply.

Here is the output as requested.

```
[FONT=monospace][COLOR=#000000]upower -i /org/freedesktop/UPower/devices/battery_BAT1 [/COLOR]
  native-path:          BAT1 
  vendor:               SDI 
  model:                PA5185U-1BRS 
  power supply:         yes 
  updated:              Thu 06 Jul 2023 18:01:45 BST (45 seconds ago) 
  has history:          yes 
  has statistics:       yes 
  battery 
    present:             yes 
    rechargeable:        yes 
    state:               discharging 
    warning-level:       none 
    energy:              22.0896 Wh 
    energy-empty:        0 Wh 
    energy-full:         31.32 Wh 
    energy-full-design:  31.68 Wh 
    energy-rate:         9.8352 W 
    voltage:             15.592 V 
    time to empty:       2.2 hours 
    percentage:          70% 
    capacity:            98.8636% 
    technology:          lithium-ion 
    icon-name:          'battery-full-symbolic' 
  History (charge): 
    1688662905  70.000  discharging 
    1688664096  0.000   unknown 
  History (rate): 
    1688662905  9.835   discharging 
    1688664096  0.000   unknown

[/FONT]
```

Trouble is nowadays even if a battery is labelled as a legitimate supplier that is no guaranty even if one pays a higher price.

This is the first charge cycle.

Geoff

---

### Post by #&amp;thj^% on 2023-07-06
> **Geoff_Lane said:**
> 
Trouble is nowadays even if a battery is labelled as a legitimate supplier that is no guaranty even if one pays a higher price.

This is the first charge cycle.

Geoff
Agreed, but there are some very reputable battery suppliers out there
And your still over what you say is/was the original battery voltage. (If was like 14.4 14.6 even 14.8 i would have less of a concern)
Kind Sir i would with certainty at least talk to the supplier with your findings, and check the heat from the battery while charging.
In it's old age it needs to be pampered with voltage, and not an over voltage. (it will find the first weak spot on your board in short time)

---

### Post by Geoff_Lane on 2023-07-12
> **1fallen said:**
> Agreed, but there are some very reputable battery suppliers out there
And your still over what you say is/was the original battery voltage. (If was like 14.4 14.6 even 14.8 i would have less of a concern)
Kind Sir i would with certainty at least talk to the supplier with your findings, and check the heat from the battery while charging.
In it's old age it needs to be pampered with voltage, and not an over voltage. (it will find the first weak spot on your board in short time)

I think the 14.4 or 14.8 voltage listing is down to the lithium battery cells being rated at 3.6/3.7 volts.

I've subsequently been able to check readings on a HP laptop (same motherboard as my Toshiba) which has an original battery.  It's battery is shown as 14.6 volts and using your suggested commands it too reaches over 16 volts when fully charged so guess mine is OK.

Like you I am cautious of voltages, I do not like items that get too hot during use, my laptop does not feel particularly warm, battery feels fine.

Appreciate your input, many thanks,

Geoff

---

