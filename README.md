# ScrApify

ScrApify is a gem which scraps static html pages and exposes them as JSON APIs

This is a sample Rails application using scrapify to expose data in static page via Models or JSON APIs

## JSON API (Rails example)

Scrapify comes with a Rack application called Jsonify which can be used in rails routes to expose scraped models as JSON.

1 Add scrapify to Gemfile

```
gem 'scrapify'
```

2 Define model to scrap data in app/models

```
class Pizza
  include Scrapify::Base
end
```

3 Model can be used to scrap and read data in the controller

```
Pizza.all

pizza = Pizza.find('mushroom')
pizza.name
pizza.image_url
```

4 Add index and show url to routes

```
  pizza_api = Jsonify.new('/pizzas', Pizza)
  get 'pizzas' => pizza_api
  get 'pizzas/:id' => pizza_api
```

Jsonify scraps url and exposes index and show as JSON APIs