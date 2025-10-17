<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vishnukart</title>
    <style>
        /* Reset */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: Arial, sans-serif; }

        body { background-color: #f5f5f5; }

        /* Header */
        header { background-color: #2874f0; color: white; padding: 10px 20px; display: flex; align-items: center; justify-content: space-between; }
        header img.logo { width: 50px; height: 50px; border-radius: 50%; margin-right: 10px; }
        .brand { display: flex; align-items: center; font-size: 24px; font-weight: bold; }

        nav a { color: white; margin: 0 10px; text-decoration: none; font-weight: bold; }
        nav a:hover { text-decoration: underline; }

        /* Main */
        .container { max-width: 1200px; margin: 20px auto; padding: 0 20px; }

        .products { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
        .product-card { background-color: white; padding: 15px; border-radius: 10px; box-shadow: 0 0 5px rgba(0,0,0,0.1); text-align: center; }
        .product-card img { width: 100%; height: 200px; object-fit: contain; margin-bottom: 10px; }
        .product-card h3 { margin-bottom: 5px; font-size: 18px; }
        .product-card p { margin-bottom: 10px; color: #555; }
        .product-card button { background-color: #fb641b; color: white; border: none; padding: 10px 15px; cursor: pointer; border-radius: 5px; font-weight: bold; }
        .product-card button:hover { background-color: #e55b15; }

        /* Footer */
        footer { background-color: #2874f0; color: white; text-align: center; padding: 15px 0; margin-top: 20px; }

        /* Cart */
        .cart { position: fixed; top: 70px; right: 20px; background-color: white; border: 1px solid #ddd; padding: 10px; width: 300px; max-height: 400px; overflow-y: auto; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.2); }
        .cart h3 { margin-bottom: 10px; }
        .cart-item { display: flex; justify-content: space-between; margin-bottom: 5px; }
    </style>
</head>
<body>

<header>
    <div class="brand">
        <img src="logo.png" alt="Vishnukart Logo" class="logo">
        Vishnukart
    </div>
    <nav>
        <a href="#home">Home</a>
        <a href="#products">Products</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </nav>
</header>

<div class="container" id="home">
    <h1>Welcome to Vishnukart</h1>
    <p>Your one-stop shop for all real products!</p>
</div>

<div class="container" id="products">
    <h2>Products</h2>
    <div class="products">
        <!-- Sample Product 1 -->
        <div class="product-card">
            <img src="https://via.placeholder.com/250x200?text=Product+1" alt="Product 1">
            <h3>Product 1</h3>
            <p>₹999</p>
            <button onclick="addToCart('Product 1', 999)">Add to Cart</button>
        </div>
        <!-- Sample Product 2 -->
        <div class="product-card">
            <img src="https://via.placeholder.com/250x200?text=Product+2" alt="Product 2">
            <h3>Product 2</h3>
            <p>₹799</p>
            <button onclick="addToCart('Product 2', 799)">Add to Cart</button>
        </div>
        <!-- Sample Product 3 -->
        <div class="product-card">
            <img src="https://via.placeholder.com/250x200?text=Product+3" alt="Product 3">
            <h3>Product 3</h3>
            <p>₹499</p>
            <button onclick="addToCart('Product 3', 499)">Add to Cart</button>
        </div>
    </div>
</div>

<div class="container" id="about">
    <h2>About Vishnukart</h2>
    <p>Founded by <strong>Vishnu Dwivedi</strong>, contact: <strong>9235363760</strong>. We provide the best shopping experience with real products and easy checkout.</p>
</div>

<div class="container" id="contact">
    <h2>Contact Us</h2>
    <p>Email: contact@vishnukart.com | Phone: 9235363760</p>
</div>

<div class="cart" id="cart">
    <h3>Cart</h3>
    <div id="cart-items"></div>
    <p id="cart-total">Total: ₹0</p>
</div>

<footer>
    &copy; 2025 Vishnukart | Contact: 9235363760
</footer>

<script>
    let cart = [];

    function addToCart(name, price) {
        cart.push({name, price});
        renderCart();
    }

    function renderCart() {
        const cartItems = document.getElementById('cart-items');
        cartItems.innerHTML = '';
        let total = 0;
        cart.forEach((item, index) => {
            const div = document.createElement('div');
            div.className = 'cart-item';
            div.innerHTML = ${item.name} - ₹${item.price} <button onclick='removeItem(${index})'>x</button>;
            cartItems.appendChild(div);
            total += item.price;
        });
        document.getElementById('cart-total').innerText = Total: ₹${total};
    }

    function removeItem(index) {
        cart.splice(index, 1);
        renderCart();
    }
</script>

</body>
</html>
