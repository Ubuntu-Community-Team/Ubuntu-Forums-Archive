---
title: "&quot;wacom-tools&quot; doesn't see working X11 &quot;devices&quot;"
date: 2010-04-05
forum: Hardware
---

### Post by SaintDanBert on 2010-04-05
My laptop is a "tablet PC" with a built-in Wacom digitizer tablet. My Ubuntu Jaunty install detects the hardware well enough that X11 runs and most of the tablet features operate. I need **wacom-tools** to fine-tune the configuration. Here the trouble starts.

Wacom-tools complains that there are no devices available. I've seen threads that mention confusion between what HAL and X11 detect and what wacom-tools expects. I've tried to follow the corrective action instructions without success. Clearly I'm missing something in the details. (Or the nut is loose in the ops chair...)

Can someone help me sort this out?

Here are some details:

1.  I've attached the results of the following
```

sudo xinput list > xinput_list.txt

```

2.  I've attached a copy of my wacom /etc/hal/fdi/policy file

If you want or need more, just tell me what to send and how to generate whatever it is.

Thanks,
~~~ 0;-Dan

---

