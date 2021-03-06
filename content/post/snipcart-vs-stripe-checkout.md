+++
Categories = []
date = "2016-09-04T16:50:00+00:00"
description = ""
draft = true
excerpt = ""
tags = []
title = "Snipcart Vs Stripe Checkout"
[[author]]
bio = "CEO and Co-founder of <a href='https://forestry.io' title='Forestry.io CMS'>Forestry.io</a>. Web developer, recovering freelancer."
img = "/images/Scott_Gallant.jpg"
name = "Scott Gallant"
twitter = "https://twitter.com/scottgallant"
[[suggested]]
link = ""
title = ""
[[suggested]]
link = ""
title = ""
[[suggested]]
link = ""
title = ""

+++
# Which online payment solution should you use for your static site?

---

If you're developing an online store, you'll know that these days there are more options than ever to handle payments. It's a classic example of how multiple standards proliferate[^1]. So which one should _you_ use?

One of the lesser known solutions for building your online store is using one of the many static-site generators out there like the GitHub Pages favorite, [Jekyll](https://jekyllrb.com/).

Using a static-site generator brings many advantages over heavier solutions like WordPress. For one, developing a static site is generally much faster than having to deal with many plugins, endless configuration of themes, databases, et cetera... This results in a quicker turnaround and faster time to market.

But this raises the question, since there are no plugins or ways to interact with the server, how does one integrate an online payments solution on a static platform? Thankfully, there's a new breed of integrated payment companies like [Snipcart](https://snipcart.com/) and [Stripe](https://stripe.com/) that provide all you'll need to make your own store.

## Choosing the right platform

Although these platforms seemingly provide similar features and integration, they have key differences that will define which one is the right solution for you. Let's look at some of these differences, starting with how you can accept payments.

#### Payment Gateways

* Snipcart allows you to accept payments from all the major payment gateway providers (PayPal, Authorize.net, PaySafe, etc... And yes, even Stripe).

* In contrast, Stripe allows you to accept payments through credit cards directly. If mobile payments are important to you, Stripe offers great integration with Apple Pay and Android Pay. They also offer a few other payment gateways like Bitcoin, Alipay and ACH.

**Takeaway**<br>
Snipcart allows for more flexibility in regards to the choice of payment gateways offered. They also support PayPal which can be very important to some businesses while Stripe does not.

#### Front-end website integration

* Snipcart's checkout window uses by default the ```snipcart.css``` theme which doesn't necessarily integrate well with all colour schemes/website designs. You can however roll out your own theme quite easily and customize the look to your heart's content. This means there is some additional configuration needed and will require some mild CSS chops.

* Stripe's embedded platform, Checkout, provides a neutral and easy to use payment form. It offers little in the way of customization besides adding your logo at the top of the dialog. It is also possible to create your own forms with Stripe.js but the process is a little more involved and aimed at experienced developers.

**Takeaway**<br>
Both platforms offer great front-end solutions targeted at slightly different audiences. Stripe's Checkout is a no-nonsense, easy to use out-of-the-box experience aimed at everyone with no particular configuration required.

With Snipcart you have more flexibility by default which allows you to get hands-on with the styling easily however you will need some CSS knowledge and a bit more time to make everything look how you want it to.

#### Admin Dashboard

![Snipcart's Dashboard](http://i.imgur.com/0RjmpE8.png)

* Snipcart's dashboard features a dual pane layout with all your store related operations on one side and all your account settings on the other. Small nitpicking here but I find that the dual pane system requires more clicking and feels a bit clunky.

![Stripe's Dashboard](http://i.imgur.com/bVufSbo.png)

* Stripe's on the other hand makes use of a simple and clean unified layout reminiscent of a macOS application. A notable feature I personally find very useful is the global search bar which makes it incredibly easy to sift through all your customers, orders, etc...

**Takeaway**<br>
Snipcart and Stripe have excellent administrator dashboards with quick and easy access to all the common features you'd expect. Choosing which one you like better is a matter of personal preference so I recommend taking a close look at the two solutions. Personally, I think Stripe's solution is slightly superior overall in terms of design and user experience.

#### Pricing

* Snipcart offers two different plans, Standard and "I am special". The standard plan charges a 2% fee per transaction **in addition** to any fees incurred by the choice of payment gateways. If your total sales for the month are under $500, the 2% is replaced by a $10 fee. The "I am special" plan offers fixed pricing for large businesses.

* Like Snipcart, Stripe offers two distinct plans, Pay as you Go and Enterprise. The Pay as you Go plan charges a 2.9% fee + $0.30 with no other fees associated for payment gateways.

For easy visualization, we created a small table to illustrate each platform's pricing and fees.

| Pricing            | Snipcart                                                         | Stripe                         | Total                                |
| ------------------ | ---------------------------------------------------------------- | ------------------------------ | ------------------------------------ |
| $10 (Credit Card)  | 2% Snipcart fee + 2.9% + $0.30 per transaction (using PayPal)    | 2.9% + $0.30 per transaction   | Snipcart: $10.35<hr>Stripe: $10.33   |

**Takeaway**<br>
Both platforms offer compelling pricing options however Stripe may be slightly cheaper in the long run depending on your choice of payment gateway.

#### Setup

* Snipcart's installation is incredibly easy and straightforward. Simply link their `snipcart.min.js` script and optionally the default `snipcart.min.css` theme before the `<head>` closing tag of your website and you are ready to go! Don't forget to include your API key with the `snipcart.min.js` script. Note that Snipcart also makes use of jQuery, so make sure you have it included in your page.

* In contrast, setting up Stripe is a bit more time consuming and requires the use of an actual server to accept payments. If you do not already have a VPS, you can use a PaaS like Heroku to host your code for free, keeping setup time and costs down.

**Takeaway**<br>
All-in-all, Snipcart is most definitely the easiest to install out of the two products. The fact the is does not require any external server or backend gives it a clear advantage over Stripe.

Check out our example integration guides below for both [Snipcart](#!) and [Stripe](#!) to get a feel for which solution you might prefer.

#### Support & Documentation

Here, Snipcart and Stripe have comparable offerings. Both services offer live chat with fast response from the support staff. I've found the documentation easy to navigate through and well written with plenty of code examples.

One thing I liked about Stripe is their searchable knowledge base whereas Snipcart only offers a regular F.A.Q. but once again, this is only personal preference and shouldn't affect your decision.


## Integrations
---

In this section, we'll look at how we can integrate Snipcart and Stripe into your favorite static-site workflow. For this article, we'll use [Jekyll](#!) but you can also use other generators like [Hugo](#!).

**What you'll need:**
* [Ruby](https://www.ruby-lang.org/en/downloads/) `v2.x or higher`
* [RubyGems](https://rubygems.org/pages/download) `latest`
* [Node](https://nodejs.org/) `v4.5.0 LTS or higher recommended`

Once you have those installed, we can move on to the next step where we will install Jekyll and create a new project.

#### Creating our project
Let's start by making sure Jekyll is properly installed on your system. Open a command prompt and type this command.

```sh
$ gem install jekyll
```

Once you have Jekyll installed, we can our website project with the following command.

```sh
$ jekyll new my-online-shop
```

Jekyll will automatically pull in all the required files and dependencies. Once that is done, `cd` into your project's directory and run the `serve` command to view your website.

```sh
$ cd my-online-shop && jekyll serve
```
#### Storing our products data

Now we can start to build our shop! We'll use collections to store our products data. To do that, open up the `_config.yml` file and add the `collections` field with the name of your collection; here we'll use `products`. We'll also set the `output` key to `true` to allow us to create individual pages for each products later on.

While we're tampering with the configuration, let's also include our api key(s) for easy access. Create a new `api_key` field with your public key. This will allow us to reference your key later on using the `site.api_key` variable.

The final output should look like so:

```
api_key: your-key-here

collections:
  products:
    output: true
```

At this point, I recommend restarting the Jekyll server to ensure the changes to the `_config.yml` are properly loaded. Once that is done, we can start creating some products.

Start by making a new directory with the name of your collection and prepend it with an underscore. In our case, it would look like `_products`.

Create a new file inside the directory we've just made and name with the name of your product for easy identification. We'll use `example-product.md` for this article. We can specify all of our product's details in the YAML Front Matter like so:

```YAML
---
name: Example product
price: 2.99
slug: example-product
sku: 1
image: https://placekitten.com/500/500
layout: product
description: Aliqua dolor proident ullamco in duis ex qui occaecat qui occaecat elit nulla.
---

Dolore fugiat qui ad cupidatat adipisicing nulla adipisicing est ut minim dolore cupidatat excepteur tempor aliquip amet culpa. Exercitation excepteur magna ad tempor enim eu pariatur commodo dolor consectetur reprehenderit. Lorem esse laborum laborum nisi sint ipsum nisi anim incididunt cillum sit. Veniam nulla aliqua et aliquip incididunt velit commodo pariatur do deserunt anim deserunt ex ullamco esse.
```

That's it! We're now ready to display all of our products on our website. Feel free to create a few additional test products for better visualization of the website will look.

#### Displaying the products

In this section, we'll cover two different methods for displaying our products, namely listing them all on one page and displaying them one at a time inside their own individual pages. Let's start with the former.

**Creating our store's index**<br>
Listing all of our products on one page is simply a matter of looping through each product inside of our `_products` directory. Thankfully, Jekyll's templating engine, [Liquid](#!) provides an easy way to do just that.

Start by creating a new `item.html` file inside of your `_includes` folder. This will serve as a reusable layout to display all of our products details.

```html
<div class="col-xs-12 col-md-4">
  <div class="card">
    <div class="card-image">
      <img class="img-responsive" src="{{ product.image }}" alt="{{ product.name }}">
    </div><!-- card image -->

    <div class="card-content">
      <span class="card-title">{{ product.name }}</span>
      <span class="card-subtitle">${{ product.price }}</span>
      {{ product.description }}
    </div><!-- card content -->
    <div class="card-action">
      <a href="{{ site.baseurl }}{{ product.url }}">View</a>
      <a href="#">Purchase</a>
    </div><!-- card actions -->
  </div>
</div>
```
This might not look very good right now but we can fix that with some simple CSS. Add the following to your `_layout.scss` file:

```CSS
/***
* Simple grid
*/
.row {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.col {
  flex-basis: 100%;
}

@media screen and (min-width: 800px) {
  .col {
    flex: 1;
  }
  .col-33 {
    flex: 0 0 33.3333%;
    max-width: 33.3333%;
  }

}

/***
* Cards
*/
.card .card-image{
    overflow: hidden;
}

.card{
    margin: 10px 5px;
    position: relative;
    -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
    -moz-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
    box-shadow: 4 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
}

.card .card-content {
    padding: 10px;
}

.card .card-content .card-title {
    display: block;
    font-size: 24px;
}

.card .card-content .card-subtitle {
    display: block;
    font-size: 14px;
}

.card .card-action {
    padding: 20px;
    border-top: 1px solid rgba(160, 160, 160, 0.2);
}

.card .card-action a {
    font-size: 15px;
    text-transform:uppercase;
    margin-right: 20px;
}

.card .card-action a:hover {
    text-decoration:none;
}
```

#### Using Stripe

#### Using Snipcart

## Conclusion
---

Overall, I think you should make your decision based on how important each feature is to you.

Snipcart offers great flexibility with a wide variety of payment gateways and lets you customize the look and feel of your checkout experience. If having PayPal as a payment option is core to your business then Snipcart will likely be your best option. Integration is also arguably easier than Stripe's so if time is of the essence, Snipcart can be set-up very quickly and easily.

Stripe provides a clean and simple checkout flow however it offers little in the way of customization or payment gateways. If you plan on accepting credit cards or Bitcoins as your sole method of payment then Stripe is a great option. Since Stripe requires a server to generate tokens, it's integration might be a little more time consuming and will require maintenance in the long term.

#### Footnotes
[^1]: [xkcd: Standards](https://xkcd.com/927/)
