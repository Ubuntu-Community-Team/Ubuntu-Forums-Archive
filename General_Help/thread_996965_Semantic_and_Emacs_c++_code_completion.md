---
title: "Semantic and Emacs c++ code completion"
date: 2008-11-29
forum: General Help
---

### Post by aliam13_2 on 2008-11-29
Hi,

I am using Intrepid and have installed semantic from the repository. I am using emacs to write c++ code and would like some form of reminding me what parameters functions have, also code completion would be nice. I finally found that I can load the semantic system via
M-x load-library semantic

Now it seems that I should be able to do
M-x semantic-complete-analyze-inline

This would provide some of the functionality that I would like. However, this breaks. I get the following error:
Wrong type argument: syntax-table-p, nil

Does anyone know how to use semantic - I have found the documentation hard to follow and the main website does not seem to help much. Does anyone know what this error means or how to fix it?

Thanks
Liam

---

