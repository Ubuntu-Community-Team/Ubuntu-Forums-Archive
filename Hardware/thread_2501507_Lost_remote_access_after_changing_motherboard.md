---
title: "Lost remote access after changing motherboard"
date: 2024-10-10
forum: Hardware
---

### Post by manmath on 2024-10-10
Dear All,
The motherboard of Ubuntu system went bad. The system was on warranty so it got replaced by an exactly same model. But since then I'm unable to access it remotely on ssh. The system has been in use as a local server.

---

### Post by TheFu on 2024-10-11
The system ssh keys have changed.  Did the OS version change?  Did the HDD change? Did the userid change? Which ubuntu release and which ubuntu flavor is being used on both sides?

** Not enough information provided.  **

BTW, "exactly same model" usually doesn't mean exactly the same chips inside unless it was a business computer and contractually guaranteed to have the exact same chips used.  Consumer computers will have the same model, but have different internal components because the prices for different chips fluctuates daily, so the manufacturer will buy whatever 20,000 chips are cheapest on any specific day that meets their requirements.  

To put that into clear terms, 
Dell sells vostro, inspiron, latitude and a few other "lines"  Of those lines, only Latitude is "business" and the same chips will be used for about 3 yrs in the same model of Latitude computer they sell.  The Inspiron and Vostro lines are consumer, so you get whatever happened to be available when they did their purchase contracts.

Hope that clarifies some things. In a corporate environment, we had to explain this to our purchasing department every time there was a new large purchase. Sometimes we'd specify a very specific model in the business line and in an attempt to save money, the purchasing people would point out that for $100 less, we could get a different computer that was listed as fast or even faster than the model we needed.  Then we get to explain about OS images and identical drivers and being able to fix most issues by re-imaging the OS - none of that is possible if the non-business-line versions were used.

---

