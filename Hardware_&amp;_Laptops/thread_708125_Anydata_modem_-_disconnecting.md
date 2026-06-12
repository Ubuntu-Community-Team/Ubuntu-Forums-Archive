---
title: "Anydata modem - disconnecting"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by donROGALesko on 2008-02-26
I've Ubuntu 7.04 2.6.20-15-generic and modem Anydata. I configured it after reading this ([http://jk.ufisa.uninett.no/anydata/](http://jk.ufisa.uninett.no/anydata/)), but I get disconnected after 30 sec.

```
Feb 25 15:38:06 localhost pppd[5742]: pppd 2.4.4 started by root, uid 0
Feb 25 15:38:07 localhost chat[5744]: abort on (BUSY)
Feb 25 15:38:07 localhost chat[5744]: abort on (NO CARRIER)
Feb 25 15:38:07 localhost chat[5744]: abort on (VOICE)
Feb 25 15:38:07 localhost chat[5744]: abort on (NO DIALTONE)
Feb 25 15:38:07 localhost chat[5744]: abort on (NO DIAL TONE)
Feb 25 15:38:07 localhost chat[5744]: abort on (NO ANSWER)
Feb 25 15:38:07 localhost chat[5744]: abort on (DELAYED^M)
Feb 25 15:38:07 localhost chat[5744]: send (ATZ^M^M)
Feb 25 15:38:07 localhost chat[5744]: expect (OK)
Feb 25 15:38:07 localhost chat[5744]: ATZ^M^M
Feb 25 15:38:07 localhost chat[5744]: OK
Feb 25 15:38:07 localhost chat[5744]:  -- got it 
Feb 25 15:38:07 localhost chat[5744]: send (ATDT#777^M)
Feb 25 15:38:08 localhost chat[5744]: expect (^M)
Feb 25 15:38:08 localhost chat[5744]: ^M
Feb 25 15:38:08 localhost chat[5744]:  -- got it 
Feb 25 15:38:08 localhost chat[5744]: send (CONNECT^M)
Feb 25 15:38:09 localhost chat[5744]: expect (dc^M)
Feb 25 15:38:09 localhost chat[5744]: 
Feb 25 15:38:09 localhost chat[5744]: ATDT#777^M^M
Feb 25 15:38:09 localhost chat[5744]: CONNECT^M
Feb 25 15:38:11 localhost chat[5744]: ~^?}#@!}!}!} }5}"}&} } } } }#}%B#}%}%}&Dd^\=})}+~~^?}#@!}!}"} }5}"}&} } } } }#}%B#}
Feb 25 15:38:15 localhost chat[5744]: %}%}&Dd^\=bb~~^?}#@!}!}#} }5}"}&} } } } }#}%B#}%}%}&Dd^\=4=~~^?}#@!}!}$} }5}"}&} } }
Feb 25 15:38:19 localhost chat[5744]:  } }#}%B#}%}%}&Dd^\=41~~^?}#@!}!}%} }5}"}&} } } } }#}%B#}%}%}&Dd^\=bn~~^?}#@!}!}&} }
Feb 25 15:38:23 localhost chat[5744]: 5}"}&} } } } }#}%B#}%}%}&Dd^\=^I}'~~^?}#@!}!}'} }5}"}&} } } } }#}%B#}%}%}&Dd^\=_X~~^?
Feb 25 15:38:25 localhost chat[5744]: }#@!}!}(} }5}"}&} } } } }#}%B#}%}%}&Dd^\=^I}>~~^?}#@!}!})} }5}"}&} } } } }#}%B#}%}%
Feb 25 15:38:54 localhost chat[5744]: alarm
Feb 25 15:38:54 localhost chat[5744]: Failed
Feb 25 15:38:55 localhost pppd[5742]: Exit.
```

---

