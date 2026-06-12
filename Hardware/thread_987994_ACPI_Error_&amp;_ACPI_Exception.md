---
title: "ACPI Error &amp; ACPI Exception"
date: 2008-11-20
forum: Hardware
---

### Post by hobong on 2008-11-20
Hi I Have something weird in my computer 
here's the ouput from dmesg :

sofian@cinema:~$ dmesg 
> ..... sniped ...
[145277.309462] ACPI Error (psargs-0355): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
[145277.309475] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node f7c49450), AE_NOT_FOUND
[145277.309520] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]
[148479.016284] ACPI Error (psargs-0355): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
[148479.016297] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node f7c49450), AE_NOT_FOUND
[148479.016339] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]
[148713.315026] ACPI Error (psargs-0355): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
[148713.315062] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node f7c49450), AE_NOT_FOUND
[148713.315107] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]
[149557.767726] ACPI Error (psargs-0355): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
[149557.767761] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node f7c49450), AE_NOT_FOUND
[149557.767804] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]
[149746.678578] ACPI Error (psargs-0355): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
[149746.678591] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node f7c49450), AE_NOT_FOUND
[149746.678635] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]

and for your information might be useful here's the ouput of lspci -vv I attached in this message.

Thanks for the Help

---

