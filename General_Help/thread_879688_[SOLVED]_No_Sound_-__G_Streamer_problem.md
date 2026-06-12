---
title: "[SOLVED] No Sound -  G Streamer problem"
date: 2008-08-04
forum: General Help
---

### Post by Dyffo on 2008-08-04
I first posted this enquiry under " Multi Media and Video" but now feel that this has become a General question.
 After I installed upgrades I lost my Sound with the error message " NO VOLUME CONTROL G STREAMER PLUGINS AND OR DEVICES FOUND ". It seems that there are many of us with this problem. I have tried numerous suggestions in various posts - but nothing has resolved my problem.
 I have found however that if I run  UBUNTU from my installation CD - I have sound !!!!!. So can anyone tell me how I can reinstall UBUNTU from the cd or wherever WITHOUT LOSING ALL MY DATA AND PROGRAMMES, which have taken many months to get together.
I wait in eager anticipation for any helpful suggestions.:confused:

---

### Post by Dyffo on 2008-08-05
THIS SOVED MY PROBLEM !!!!!!!!!!!!!!!!!!!!!!


Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)

---

