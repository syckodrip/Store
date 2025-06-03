

<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sycko - Luxury Gen Z Fashion</title>
  <style>
    /* Reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      scroll-behavior: smooth;
    }

    body, html {
      height: 100%;
      font-family: 'Poppins', sans-serif;
      background: url('your-background.jpg') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
      line-height: 1.6;
      overflow-x: hidden;
    }

    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.7);
      z-index: 0;
    }

    .content {
      position: relative;
      z-index: 1;
      max-width: 1200px;
      margin: auto;
      padding: 2rem;
    }

    /* Preloader */
    .preloader {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #000;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      animation: fadeOut 1s ease forwards;
    }

    @keyframes fadeOut {
      to { opacity: 0; visibility: hidden; }
    }

    .content.hide {
      opacity: 0;
    }

    .content.show {
      opacity: 1;
      transition: opacity 1s ease-in-out;
    }

    /* Hero Section */
    header.hero {
      text-align: center;
      padding: 20vh 2rem 10vh;
    }

    header h1 {
      font-size: 3rem;
      font-weight: bold;
      color: #00ffe7;
      margin-bottom: 1rem;
    }

    header p {
      font-size: 1.2rem;
      color: #ccc;
      margin-bottom: 2rem;
    }

    .btn {
      display: inline-block;
      background: #00ffe7;
      color: #000;
      padding: 0.8rem 2rem;
      border-radius: 30px;
      font-weight: bold;
      text-decoration: none;
      transition: background 0.3s ease;
    }

    .btn:hover {
      background: #0fffc1;
    }

    /* Products Grid */
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
      padding: 2rem;
      margin-top: 2rem;
    }

    .product-card {
      background: #1a1a1a;
      border-radius: 10px;
      overflow: hidden;
      text-align: center;
    }

    .product-card img {
      width: 100%;
      height: auto;
      object-fit: cover;
    }

    .product-info {
      padding: 1rem;
    }

    .product-info h3 {
      font-size: 1.2rem;
      margin-bottom: 0.5rem;
    }

    .product-info .price {
      color: #ccc;
      font-size: 1rem;
      margin-bottom: 0.5rem;
    }

    .product-info select,
    .product-info input[type="number"],
    .product-info button {
      margin-top: 1rem;
      padding: 0.5rem 1rem;
      border-radius: 30px;
      border: none;
      cursor: pointer;
      font-size: 0.9rem;
      background: #00ffe7;
      color: #000;
      font-weight: bold;
      transition: 0.3s;
    }

    .product-info button:hover {
      background: #0fffc1;
    }

    .note {
      font-size: 0.8rem;
      color: #aaa;
      margin-top: 0.5rem;
    }

    /* Shopping Cart Modal */
    .cart-icon {
      position: fixed;
      bottom: 20px;
      right: 20px;
      cursor: pointer;
      font-size: 1.5rem;
      color: #00ffe7;
      background: #fff;
      padding: 1rem;
      border-radius: 50%;
      box-shadow: 0 0 10px #00ffe7;
      z-index: 999;
    }

    .cart-modal {
      display: none;
      position: fixed;
      top: 60px;
      right: 80px;
      width: 300px;
      background: #111;
      border-radius: 10px;
      padding: 1rem;
      box-shadow: 0 0 10px rgba(0, 255, 231, 0.3);
      z-index: 999;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1rem;
      border-bottom: 1px solid #333;
      padding-bottom: 0.5rem;
    }

    .cart-actions button {
      background: none;
      color: #00ffe7;
      border: none;
      font-size: 1.2rem;
      cursor: pointer;
    }

    .cart-total {
      text-align: right;
      margin-top: 1rem;
      font-weight: bold;
    }

    .order-note {
      font-size: 0.8rem;
      color: #ff4ecd;
      margin-top: 1rem;
    }

    footer.footer {
      margin-top: 4rem;
      text-align: center;
      font-size: 0.9rem;
      color: #555;
    }

    footer.footer a {
      color: #00ffe7;
      text-decoration: underline;
    }

    @media (max-width: 600px) {
      .cart-modal {
        right: 20px;
        width: 90%;
      }

      .cart-icon {
        right: 15px;
        bottom: 15px;
      }
    }
  </style>
</head>
<body>

  <!-- Preloader -->
  <div class="preloader" id="preloader"></div>

  <!-- Main Content -->
  <div class="content hide" id="mainContent">

    <!-- Homepage -->
    <section id="homepage" class="hero">
      <h1>Sycko</h1>
      <p>Luxury meets Gen Z fashion.</p>
      <button onclick="showProducts()" class="btn">Shop Now</button>
    </section>

    <!-- Products Section -->
    <section id="productPage" style="display: none;">
      <h2 style="text-align:center; margin-bottom: 2rem;">Our Collection</h2>
      <div class="products" id="products">
        <!-- Filled by JS -->
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      Follow us on Instagram: <a href="https://instagram.com/syckofashion" target="_blank">@syckofashion</a>
    </footer>

  </div>

  <!-- Floating Cart Icon -->
  <div class="cart-icon" onclick="toggleCart()">🛒 (<span id="cart-count">0</span>)</div>

  <!-- Shopping Cart Modal -->
  <div id="cartModal" class="cart-modal">
    <h3>Your Cart</h3>
    <div id="cartItems"></div>
    <div class="cart-total">Total: ₹<span id="cartTotal">0</span></div>
    <div class="order-note">Order only via Instagram DM</div>
  </div>

  <script>
    // Product Data
    const products = [
      {
        id: 1,
        name: "Stranger Things T-Shirt",
        price: 799,
        caption: "Immerse yourself in elevated comfort with this relaxed-fit Stranger Things tee—crafted from premium heavy gauge bio-cotton for a soft, breathable feel.",
        image: "product1.jpg"
      },
      {
        id: 2,
        name: "Minecraft T-Shirt",
        price: 749,
        caption: "Built for real-world adventures—this relaxed-fit Minecraft tee is crafted from ultra-soft, heavy gauge bio-cotton, blending pixel-perfect design with all-day breathable comfort.",
        image: "product2.jpg"
      },
      {
        id: 3,
        name: "Cyberpunk Jacket",
        price: 1299,
        caption: "Bold and futuristic jacket inspired by digital culture. Perfect for any streetwear look.",
        image: "product3.jpg"
      },
      {
        id: 4,
        name: "Neon Logo Hoodie",
        price: 899,
        caption: "Stand out in our neon logo hoodie — ultra-comfy cotton with glowing details.",
        image: "product4.jpg"
      },
      {
        id: 5,
        name: "Mirror Sneakers",
        price: 1499,
        caption: "Step into the future of footwear with these reflective mirror sneakers.",
        image: "product5.jpg"
      }
    ];

    let cart = [];

    window.onload = () => {
      const savedCart = localStorage.getItem("cart");
      if (savedCart) cart = JSON.parse(savedCart);
      renderProducts();
      updateCart();
    };

    function saveCart() {
      localStorage.setItem("cart", JSON.stringify(cart));
    }

    function showProducts() {
      document.getElementById("homepage").style.display = "none";
      document.getElementById("productPage").style.display = "block";
    }

    function renderProducts() {
      const container = document.getElementById("products");
      container.innerHTML = "";

      products.forEach(product => {
        const div = document.createElement("div");
        div.className = "product-card";

        div.innerHTML = `
          <img src="${product.image}" alt="${product.name}">
          <div class="product-info">
            <h3>${product.name}</h3>
            <div class="price">₹${product.price}</div>
            <select id="size-${product.id}">
              <option value="small">Small</option>
              <option value="medium">Medium</option>
              <option value="large">Large</option>
            </select>
            <br>
            <input type="number" id="qty-${product.id}" value="1" min="1" style="margin-top: 0.5rem; width: 60px; border-radius: 30px; text-align: center; border: none; background: #222; color: #fff;">
            <br>
            <button onclick="addToCart(${product.id}, '${product.name}', ${product.price})">Add to Cart</button>
            <div class="note">Only via Instagram</div>
          </div>
        `;
        container.appendChild(div);
      });
    }

    function addToCart(id, name, price) {
      const size = document.getElementById(`size-${id}`).value;
      const qty = parseInt(document.getElementById(`qty-${id}`).value);

      const existing = cart.find(item => item.id === id && item.size === size);
      if (existing) {
        existing.qty += qty;
      } else {
        cart.push({ id, name, price, size, qty });
      }

      saveCart();
      updateCart();
      toggleCart(); // Auto-open cart
    }

    function updateCart() {
      const cartItems = document.getElementById("cartItems");
      const cartTotal = document.getElementById("cartTotal");
      const cartCount = document.getElementById("cart-count");

      cartItems.innerHTML = "";
      let total = 0;

      cart.forEach((item, index) => {
        total += item.price * item.qty;
        cartItems.innerHTML += `
          <div class="cart-item">
            <span>${item.name}<br><small>Size: ${item.size} | Qty: ${item.qty}</small></span>
            <div class="cart-actions">
              <button onclick="changeQty(${index}, -1)">−</button>
              <button onclick="changeQty(${index}, 1)">+</button>
              <button onclick="removeItem(${index})">🗑️</button>
            </div>
          </div>
        `;
      });

      cartTotal.textContent = total.toFixed(2);
      cartCount.textContent = cart.reduce((acc, item) => acc + item.qty, 0);
    }

    function changeQty(index, delta) {
      cart[index].qty += delta;
      if (cart[index].qty <= 0) cart.splice(index, 1);
      saveCart();
      updateCart();
    }

    function removeItem(index) {
      cart.splice(index, 1);
      saveCart();
      updateCart();
    }

    function toggleCart() {
      const cartModal = document.getElementById("cartModal");
      cartModal.style.display = cartModal.style.display === "block" ? "none" : "block";
    }

    function saveCart() {
      localStorage.setItem("cart", JSON.stringify(cart));
    }

    // Loader
    window.addEventListener("load", () => {
      setTimeout(() => {
        document.getElementById("preloader").style.display = "none";
        document.getElementById("mainContent").classList.remove("hide");
        document.getElementById("mainContent").classList.add("show");
      }, 1000);
    });
  </script>

</body>
</html>
