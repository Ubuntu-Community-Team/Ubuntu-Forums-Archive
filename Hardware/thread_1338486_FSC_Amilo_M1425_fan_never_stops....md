---
title: "FSC Amilo M1425 fan never stops..."
date: 2009-11-26
forum: Hardware
---

### Post by ronzo on 2009-11-26
On my M1425 the fan never stops completely. In this forum I found an archived Thread about this problem but another amilo model: [http://ubuntuforums.org/showthread.php?t=482900&highlight=AMILO+Pro+V3515](http://ubuntuforums.org/showthread.php?t=482900&highlight=AMILO+Pro+V3515)

If I follow the steps described in the archived thread, I get a DSDT.dat without a FAN-section. Only THRM shows up:

```
                    ThermalZone (THRM)
                    {
                        Method (KELV, 1, NotSerialized)
                        {
                            If (LGreater (Arg0, 0x7F))
                            {
                                XOr (Arg0, 0xFF, Local0)
                                Add (Local0, 0x01, Local0)
                                Multiply (Local0, 0x0A, Local0)
                                Subtract (0x0AAC, Local0, Local1)
                            }
                            Else
                            {
                                Multiply (Arg0, 0x0A, Local0)
                                Add (Local0, 0x0AAC, Local1)
                            }

                            Return (Local1)
                        }

                        Method (_TMP, 0, NotSerialized)
                        {
                            Return (KELV (THPP))
                        }

                        Method (_CRT, 0, NotSerialized)
                        {
                            Return (KELV (0x55))
                        }
                    }
                }

```

Does anybody know if changing a value in this section could help me?

Thank you very much in advance for your answers!

---

