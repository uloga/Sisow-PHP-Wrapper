# Sisow-PHP-Wrapper
### Bijgevoegd vindt u volgende:
* sisow.cls5.php: onze standaard PHP5 wrapper class, gebaseerd op de REST API;
* payment.php: een voorbeeld welke gebruikmaakt van de wrapper class;
* REST API 3.2.1: de laatste versie van de REST API.

### In het kort de te volgen stappen:
1. Vul een dropdown (select) met de beschikbare banken, dit kan op twee manieren:
	 1. De meest eenvoudige methode is met behulp van een op de gateway beschikbaar JavaScript (https://www.sisow.nl/Sisow/iDeal/issuers.js; volgende HTML kan daarvoor gebruikt worden: `<select name="issuerid"><script type="text/javascript" src="https://www.sisow.nl/Sisow/iDeal/issuers.js"></script></select>`);
	2. Of met behulp van de methode DirectoryRequest uit de wrapper class;
2. Instantieer de class, vul de benodigde variabelen (amount, purchaseId, description, notifyUrl, returnUrl en eventueel payment) en start de methode TransactionRequest; deze retourneert de “issuerurl” van/voor de gekozen bank; redirect naar de issuerurl;
3. Bij terugkoppeling (via de notifyurl) kan met behulp van de methode StatusRequest de status van de transactie bij onze gateway worden geverifieerd, tevens verkrijg je hieruit o.a. de bankgegevens van de betaler;
4. Bij terugkomst (via returnurl) kan op basis van succes of geen succes de betaler worden doorverwezen naar respectievelijk een “Bedankt” pagina of een “Betaling mislukt” pagina.

### Minimaal op te geven URL’s:

* notifyurl: deze URL verwacht een verwerkend script, namelijk de verwerking van de geretourneerde status. Na verwerking dient onze gateway de controle terug te krijgen.
* returnurl: na terugkomst vanuit de notifyurl wordt de klant/gebruiker doorgelinkt naar de returnurl.

API Wrapper versie datum: `05-01-2016 07:26`