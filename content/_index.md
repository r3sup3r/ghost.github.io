---
title: "Home"
description: "Home"
---

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title></title>

</head>
<style>
    </style>
</head>
<body>
    <div class="quote-container">
        {{< lead >}}<p class="quote" id="quote"></p>
        <p class="author" id="author"></p>
        <p class="source" id="source"></p>
        {{< /lead >}}

  </div>
    
   <script>
        fetch('quotes.json')
            .then(response => response.json())
            .then(quotes => {
                const quoteElement = document.getElementById("quote");
                const authorElement = document.getElementById("author");
                const sourceElement = document.getElementById("source");
                const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
                let index = 0;

                function typeWriter() {
                    if (index < randomQuote.text.length) {
                        quoteElement.innerHTML += randomQuote.text.charAt(index);
                        index++;
                        setTimeout(typeWriter, 50);
                    } else {
                        authorElement.innerHTML = "- <b>" + randomQuote.author + "</b>";
                        sourceElement.innerHTML = "<i>" + randomQuote.source + "</i>";
                    }
                }

                typeWriter();
            })
            .catch(error => console.error('Error loading quotes:', error));
/** "The only limit to our realization of tomorrow is our doubts of today.",
            "Do what you can, with what you have, where you are.",
            "Success is not final, failure is not fatal: it is the courage to continue that counts.",
            "Believe you can and you're halfway there.",
            "Act as if what you do makes a difference. It does.",
**/
    </script>
</body>
</html>

---


