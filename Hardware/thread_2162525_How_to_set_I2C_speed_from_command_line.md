---
title: "How to set I2C speed from command line?"
date: 2013-07-14
forum: Hardware
---

### Post by walao81 on 2013-07-14
Recently, I try to play some i2c device on pandaboard es with ubuntu precise, my code is worked. but seems like the i2c bus frequency is too high lead my device was hang after working a short period.

my syslog
```
Jul  5 12:46:16 my-panda kernel: [    0.637573] omap_i2c omap_i2c.4: bus 4 rev2.4.0 at 400 kHz

```

I try to find how to reduce i2c speed, but i can't find a straightforward solution, therefor, i step into the ubuntu precie source code:
```
git://kernel.ubuntu.com/ubuntu/ubuntu-precise.git
branch: ti-omap4
```

I found a function inside arch/arm/plat-omap/i2c.c, base on the function comment, look like we can set i2c speed by command line, but i have no idea how to run it. does anyone know how to do that?


```

/**
 * omap_i2c_bus_setup - Process command line options for the I2C bus speed
 * @str: String of options
 *
 * This function allow to override the default I2C bus speed for given I2C
 * bus with a command line option.
 *
 * Format: i2c_bus=bus_id,clkrate (in kHz)
 *
 * Returns 1 on success, 0 otherwise.
 */
static int __init omap_i2c_bus_setup(char *str)
{
        int ports;
        int ints[3];


        ports = omap_i2c_nr_ports();
        get_options(str, 3, ints);
        if (ints[0] < 2 || ints[1] < 1 || ints[1] > ports)
                return 0;
        i2c_pdata[ints[1] - 1].clkrate = ints[2];
        i2c_pdata[ints[1] - 1].clkrate |= OMAP_I2C_CMDLINE_SETUP;


        return 1;
}

```

---

