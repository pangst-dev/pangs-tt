<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin PANGS!T - Monitoring Pesanan Real-Time</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Segoe+UI:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* ==================== RESET & VARIABLES ==================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary: #ff6b35;
            --primary-dark: #e55a2b;
            --secondary: #2d3047;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
            --info: #17a2b8;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            --transition: all 0.3s ease;
        }
        
        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background-color: #f5f7fa;
            color: var(--dark);
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* ==================== LOGIN PAGE ==================== */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--secondary) 0%, #1a1c2f 100%);
            padding: 15px;
        }
        
        .login-box {
            background-color: white;
            border-radius: 12px;
            padding: 30px;
            width: 100%;
            max-width: 380px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .login-logo {
            text-align: center;
            margin-bottom: 25px;
        }
        
        .login-logo .logo-icon {
            color: var(--primary);
            font-size: 42px;
            margin-bottom: 12px;
        }
        
        .login-logo .logo-text {
            font-size: 26px;
            font-weight: 700;
            color: var(--secondary);
        }
        
        .login-logo .logo-text span {
            color: var(--primary);
        }
        
        .login-title {
            text-align: center;
            margin-bottom: 25px;
        }
        
        .login-title h2 {
            color: var(--secondary);
            margin-bottom: 8px;
            font-size: 22px;
        }
        
        .login-title p {
            color: var(--gray);
            font-size: 14px;
        }
        
        .login-form .form-group {
            margin-bottom: 18px;
        }
        
        .login-form label {
            display: block;
            margin-bottom: 6px;
            font-weight: 600;
            color: var(--secondary);
            font-size: 14px;
        }
        
        .login-form input {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            font-size: 15px;
            transition: var(--transition);
        }
        
        .login-form input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.1);
        }
        
        .login-btn {
            width: 100%;
            padding: 14px;
            margin-top: 10px;
            font-size: 15px;
            font-weight: 600;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .login-btn:hover {
            background: var(--primary-dark);
        }
        
        .login-error {
            color: var(--danger);
            text-align: center;
            margin-top: 12px;
            font-size: 13px;
            display: none;
        }
        
        /* ==================== ADMIN DASHBOARD ==================== */
        #adminPage {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .admin-header {
            background: linear-gradient(135deg, var(--secondary) 0%, #1a1c2f 100%);
            color: white;
            padding: 15px 0;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .admin-header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .admin-logo {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .admin-logo-icon {
            color: var(--primary);
            font-size: 22px;
        }
        
        .admin-logo-text {
            font-size: 20px;
            font-weight: 700;
        }
        
        .admin-logo-text span {
            color: var(--primary);
        }
        
        .admin-user {
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        
        .admin-avatar {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 16px;
        }
        
        .logout-btn {
            background-color: transparent;
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            padding: 6px 14px;
            border-radius: 5px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 500;
            font-size: 14px;
        }
        
        .logout-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .admin-main {
            min-height: calc(100vh - 130px);
            padding: 25px 0;
        }
        
        .admin-title {
            margin-bottom: 25px;
        }
        
        .admin-title h1 {
            font-size: 28px;
            color: var(--secondary);
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .live-badge {
            background: var(--danger);
            color: white;
            font-size: 11px;
            padding: 4px 10px;
            border-radius: 20px;
            animation: pulse 1.5s infinite;
            display: inline-flex;
            align-items: center;
            gap: 4px;
        }
        
        @keyframes pulse {
            0% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.05); }
            100% { opacity: 1; transform: scale(1); }
        }
        
        /* ==================== STATS CARDS ==================== */
        .stats-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .stat-card {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 15px;
            transition: var(--transition);
            cursor: pointer;
            border: 2px solid transparent;
        }
        
        .stat-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.12);
            border-color: var(--primary);
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            color: white;
            flex-shrink: 0;
        }
        
        .stat-icon.pending {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
        .stat-icon.processing {
            background: linear-gradient(135deg, var(--info) 0%, #138496 100%);
        }
        
        .stat-icon.completed {
            background: linear-gradient(135deg, var(--success) 0%, #1e7e34 100%);
        }
        
        .stat-icon.total {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
        }
        
        .stat-info h3 {
            font-size: 26px;
            margin-bottom: 4px;
            color: var(--secondary);
        }
        
        .stat-info p {
            color: var(--gray);
            font-size: 13px;
        }
        
        /* ==================== CONTROLS ==================== */
        .admin-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 12px;
            background-color: white;
            padding: 18px;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }
        
        .search-box {
            position: relative;
            flex: 1;
            min-width: 250px;
        }
        
        .search-box input {
            width: 100%;
            padding: 11px 18px 11px 40px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            font-size: 15px;
            transition: var(--transition);
        }
        
        .search-box input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.1);
        }
        
        .search-icon {
            position: absolute;
            left: 13px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
            font-size: 16px;
        }
        
        .filter-controls {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            overflow-x: auto;
            padding-bottom: 5px;
        }
        
        .filter-btn {
            padding: 9px 16px;
            background-color: white;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 14px;
            white-space: nowrap;
        }
        
        .filter-btn:hover {
            background-color: var(--light-gray);
        }
        
        .filter-btn.active {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            border-color: var(--primary);
        }
        
        /* ==================== ORDERS TABLE ==================== */
        .orders-table-container {
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            overflow: hidden;
            margin-bottom: 30px;
            overflow-x: auto;
        }
        
        .table-header {
            padding: 18px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .table-header h3 {
            color: var(--secondary);
            font-size: 17px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .refresh-btn {
            background: none;
            border: 1px solid var(--light-gray);
            padding: 7px 14px;
            border-radius: 6px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 500;
            font-size: 14px;
        }
        
        .refresh-btn:hover {
            background-color: var(--light-gray);
        }
        
        .refresh-btn.rotating i {
            animation: rotate 1s linear infinite;
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .orders-table {
            width: 100%;
            border-collapse: collapse;
            min-width: 1000px;
        }
        
        .orders-table thead {
            background-color: var(--light-gray);
        }
        
        .orders-table th {
            padding: 16px 12px;
            text-align: left;
            font-weight: 600;
            color: var(--secondary);
            font-size: 14px;
            border-bottom: 2px solid var(--light-gray);
        }
        
        .orders-table tbody tr {
            border-bottom: 1px solid var(--light-gray);
            transition: var(--transition);
        }
        
        .orders-table tbody tr:hover {
            background-color: rgba(255, 107, 53, 0.05);
        }
        
        .orders-table tbody tr.new-order {
            animation: highlightNew 2s ease;
            background-color: rgba(255, 107, 53, 0.1);
        }
        
        @keyframes highlightNew {
            0% { background-color: rgba(255, 107, 53, 0.3); }
            100% { background-color: rgba(255, 107, 53, 0.1); }
        }
        
        .orders-table td {
            padding: 14px 12px;
            vertical-align: middle;
            font-size: 14px;
        }
        
        .order-id {
            font-weight: 600;
            color: var(--secondary);
            font-family: monospace;
            font-size: 13px;
        }
        
        .customer-info .customer-name {
            font-weight: 600;
            margin-bottom: 3px;
            color: var(--secondary);
            font-size: 14px;
        }
        
        .customer-info .customer-phone {
            color: var(--gray);
            font-size: 13px;
        }
        
        .product-list {
            list-style: none;
            max-height: 90px;
            overflow-y: auto;
            padding-right: 5px;
            margin: 0;
        }
        
        .product-list li {
            margin-bottom: 6px;
            padding-bottom: 6px;
            border-bottom: 1px dashed var(--light-gray);
            font-size: 13px;
        }
        
        .product-list li:last-child {
            margin-bottom: 0;
            padding-bottom: 0;
            border-bottom: none;
        }
        
        /* ==================== STATUS BADGES ==================== */
        .status-badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            min-width: 85px;
            text-align: center;
        }
        
        .status-pending {
            background-color: rgba(255, 193, 7, 0.15);
            color: #b38b00;
            border: 1px solid rgba(255, 193, 7, 0.3);
        }
        
        .status-processing {
            background-color: rgba(23, 162, 184, 0.15);
            color: #0c5460;
            border: 1px solid rgba(23, 162, 184, 0.3);
        }
        
        .status-completed {
            background-color: rgba(40, 167, 69, 0.15);
            color: #155724;
            border: 1px solid rgba(40, 167, 69, 0.3);
        }
        
        .status-cancelled {
            background-color: rgba(220, 53, 69, 0.15);
            color: #721c24;
            border: 1px solid rgba(220, 53, 69, 0.3);
        }
        
        /* ==================== ACTION BUTTONS ==================== */
        .action-buttons {
            display: flex;
            gap: 6px;
        }
        
        .action-btn {
            width: 32px;
            height: 32px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            border: none;
            cursor: pointer;
            transition: var(--transition);
            color: white;
            font-size: 13px;
        }
        
        .action-btn.view {
            background: linear-gradient(135deg, var(--info) 0%, #138496 100%);
        }
        
        .action-btn.edit {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
        .action-btn:hover {
            opacity: 0.9;
            transform: scale(1.05);
        }
        
        /* ==================== NO ORDERS MESSAGE ==================== */
        .no-orders {
            text-align: center;
            padding: 50px 15px;
            color: var(--gray);
        }
        
        .no-orders i {
            font-size: 50px;
            margin-bottom: 15px;
            color: var(--light-gray);
        }
        
        .no-orders h3 {
            margin-bottom: 8px;
            color: var(--gray);
            font-size: 18px;
        }
        
        /* ==================== MODAL ==================== */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 15px;
            animation: fadeIn 0.3s ease;
            overflow-y: auto;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 12px;
            width: 100%;
            max-width: 700px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            animation: modalSlideIn 0.3s ease;
        }
        
        @keyframes modalSlideIn {
            from { transform: translateY(-30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            font-size: 24px;
            color: var(--gray);
            cursor: pointer;
            z-index: 10;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }
        
        .close-modal:hover {
            background-color: var(--light-gray);
            color: var(--dark);
        }
        
        .modal-header {
            padding: 22px 25px 12px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .modal-header h2 {
            color: var(--secondary);
            font-size: 22px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .modal-body {
            padding: 25px;
        }
        
        .order-details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 25px;
        }
        
        .detail-section {
            margin-bottom: 22px;
        }
        
        .detail-section h3 {
            color: var(--secondary);
            margin-bottom: 12px;
            font-size: 17px;
            padding-bottom: 6px;
            border-bottom: 2px solid var(--light-gray);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .detail-section h3 i {
            color: var(--primary);
        }
        
        .detail-item {
            display: flex;
            margin-bottom: 10px;
            flex-wrap: wrap;
        }
        
        .detail-label {
            font-weight: 600;
            width: 130px;
            color: var(--secondary);
            flex-shrink: 0;
            font-size: 14px;
        }
        
        .items-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 8px;
            font-size: 14px;
        }
        
        .items-table th {
            background-color: var(--light-gray);
            padding: 11px;
            text-align: left;
            color: var(--secondary);
            font-weight: 600;
            font-size: 13px;
        }
        
        .items-table td {
            padding: 11px;
            border-bottom: 1px solid var(--light-gray);
            font-size: 13px;
        }
        
        .items-table tr:last-child td {
            border-bottom: none;
        }
        
        .modal-footer {
            padding: 18px 25px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
        }
        
        .status-select {
            padding: 9px 13px;
            border-radius: 6px;
            border: 1px solid var(--light-gray);
            font-size: 15px;
            min-width: 180px;
            background-color: white;
            cursor: pointer;
            flex: 1;
        }
        
        .status-select:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        /* ==================== BUTTONS ==================== */
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 11px 22px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            font-size: 15px;
            border: none;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 12px rgba(255, 107, 53, 0.25);
        }
        
        .btn-secondary {
            background: linear-gradient(135deg, var(--secondary) 0%, #1f2135 100%);
        }
        
        /* ==================== NOTIFICATIONS ==================== */
        .notification {
            position: fixed;
            top: 15px;
            right: 15px;
            background: linear-gradient(135deg, var(--success) 0%, #1e7e34 100%);
            color: white;
            padding: 14px 22px;
            border-radius: 8px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
            z-index: 3000;
            animation: slideInRight 0.3s ease, slideOutRight 0.3s ease 4.7s;
            max-width: 320px;
            font-size: 13px;
            line-height: 1.4;
        }
        
        .notification.error {
            background: linear-gradient(135deg, var(--danger) 0%, #c82333 100%);
        }
        
        .notification.warning {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
        .notification.info {
            background: linear-gradient(135deg, var(--info) 0%, #138496 100%);
        }
        
        @keyframes slideInRight {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
        
        @keyframes slideOutRight {
            from {
                transform: translateX(0);
                opacity: 1;
            }
            to {
                transform: translateX(100%);
                opacity: 0;
            }
        }
        
        /* ==================== CONNECTION STATUS ==================== */
        .connection-status {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 13px;
            padding: 6px 12px;
            border-radius: 20px;
            background-color: rgba(40, 167, 69, 0.15);
            color: #155724;
            border: 1px solid rgba(40, 167, 69, 0.3);
        }
        
        .connection-status.offline {
            background-color: rgba(220, 53, 69, 0.15);
            color: #721c24;
            border: 1px solid rgba(220, 53, 69, 0.3);
        }
        
        .connection-status .status-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: #28a745;
            animation: blink 2s infinite;
        }
        
        .connection-status.offline .status-dot {
            background-color: #dc3545;
            animation: none;
        }
        
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }
        
        /* ==================== RESPONSIVE ==================== */
        @media (max-width: 992px) {
            .orders-table {
                min-width: 900px;
            }
            
            .modal-footer {
                flex-direction: column;
                align-items: stretch;
            }
            
            .status-select {
                width: 100%;
            }
        }
        
        @media (max-width: 768px) {
            .admin-controls {
                flex-direction: column;
                align-items: stretch;
            }
            
            .search-box {
                width: 100%;
                min-width: 100%;
            }
            
            .filter-controls {
                width: 100%;
                justify-content: flex-start;
            }
            
            .stats-cards {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .admin-title h1 {
                font-size: 24px;
            }
            
            .modal-body {
                padding: 20px;
            }
            
            .order-details-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
        }
        
        @media (max-width: 576px) {
            .stats-cards {
                grid-template-columns: 1fr;
            }
            
            .admin-header-content {
                flex-direction: column;
                align-items: flex-start;
                gap: 12px;
            }
            
            .admin-user {
                width: 100%;
                justify-content: space-between;
            }
            
            .orders-table th, 
            .orders-table td {
                padding: 11px 8px;
                font-size: 13px;
            }
            
            .action-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .action-btn {
                width: 30px;
                height: 30px;
            }
            
            .login-box {
                padding: 25px 18px;
            }
            
            .modal-content {
                max-height: 95vh;
            }
            
            .table-header {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .refresh-btn {
                align-self: flex-start;
            }
            
            .detail-label {
                width: 110px;
            }
        }
        
        @media (max-width: 400px) {
            .filter-btn {
                padding: 8px 12px;
                font-size: 13px;
            }
            
            .stat-card {
                padding: 15px;
            }
            
            .stat-icon {
                width: 45px;
                height: 45px;
                font-size: 20px;
            }
            
            .stat-info h3 {
                font-size: 22px;
            }
            
            .notification {
                max-width: 280px;
                right: 10px;
                left: 10px;
            }
        }
        
        /* ==================== SCROLLBAR ==================== */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        
        ::-webkit-scrollbar-track {
            background: var(--light-gray);
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: var(--primary-dark);
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div id="loginPage" class="login-container">
        <div class="login-box">
            <div class="login-logo">
                <div class="logo-icon">
                    <i class="fas fa-dumpling"></i>
                </div>
                <div class="logo-text">PANGS!T <span>Admin</span></div>
            </div>
            
            <div class="login-title">
                <h2>Masuk ke Dashboard</h2>
                <p>Pantau pesanan pelanggan secara real-time</p>
            </div>
            
            <form id="loginForm" class="login-form">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="admin" required>
                </div>
                
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="admin123" required>
                </div>
                
                <button type="submit" class="btn login-btn">
                    <i class="fas fa-sign-in-alt"></i> Masuk
                </button>
                
                <div id="loginError" class="login-error">
                    <i class="fas fa-exclamation-circle"></i> Username atau password salah!
                </div>
            </form>
        </div>
    </div>
    
    <!-- Admin Dashboard -->
    <div id="adminPage">
        <!-- Header -->
        <header class="admin-header">
            <div class="container">
                <div class="admin-header-content">
                    <div class="admin-logo">
                        <div class="admin-logo-icon">
                            <i class="fas fa-dumpling"></i>
                        </div>
                        <div class="admin-logo-text">PANGS!T <span>Admin</span></div>
                    </div>
                    
                    <div class="admin-user">
                        <div style="display: flex; align-items: center; gap: 10px;">
                            <div class="admin-avatar">A</div>
                            <div>
                                <div style="font-weight: 600; font-size: 15px;">Administrator</div>
                                <div style="font-size: 13px; opacity: 0.8;">PANGS!T Manager</div>
                            </div>
                        </div>
                        <div class="connection-status" id="connectionStatus">
                            <div class="status-dot"></div>
                            <span id="statusText">Online</span>
                        </div>
                        <button class="logout-btn" id="logoutBtn">
                            <i class="fas fa-sign-out-alt"></i> Keluar
                        </button>
                    </div>
                </div>
            </div>
        </header>
        
        <!-- Main Content -->
        <main class="admin-main">
            <div class="container">
                <!-- Title -->
                <div class="admin-title">
                    <h1>
                        <i class="fas fa-shopping-cart"></i> Manajemen Pesanan
                        <span class="live-badge"><i class="fas fa-circle"></i> LIVE</span>
                    </h1>
                    <p style="font-size: 14px;">
                        <span id="lastUpdateTime">Mengambil data...</span> 
                        <span id="deviceInfo" style="font-size: 12px; color: var(--gray);"></span>
                    </p>
                </div>
                
                <!-- Stats -->
                <div class="stats-cards">
                    <div class="stat-card" data-filter="pending">
                        <div class="stat-icon pending">
                            <i class="fas fa-clock"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="pendingCount">0</h3>
                            <p>Menunggu Konfirmasi</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="processing">
                        <div class="stat-icon processing">
                            <i class="fas fa-truck"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="processingCount">0</h3>
                            <p>Sedang Diproses</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="completed">
                        <div class="stat-icon completed">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="completedCount">0</h3>
                            <p>Selesai</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="all">
                        <div class="stat-icon total">
                            <i class="fas fa-chart-line"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="totalOrdersCount">0</h3>
                            <p>Total Pesanan</p>
                        </div>
                    </div>
                </div>
                
                <!-- Controls -->
                <div class="admin-controls">
                    <div class="search-box">
                        <i class="fas fa-search search-icon"></i>
                        <input type="text" id="searchOrders" placeholder="Cari pesanan, nama pelanggan, atau ID...">
                    </div>
                    
                    <div class="filter-controls">
                        <button class="filter-btn active" data-status="all">
                            <i class="fas fa-list"></i> Semua
                        </button>
                        <button class="filter-btn" data-status="pending">
                            <i class="fas fa-clock"></i> Menunggu
                        </button>
                        <button class="filter-btn" data-status="processing">
                            <i class="fas fa-truck"></i> Diproses
                        </button>
                        <button class="filter-btn" data-status="completed">
                            <i class="fas fa-check-circle"></i> Selesai
                        </button>
                        <button class="filter-btn" data-status="cancelled">
                            <i class="fas fa-times-circle"></i> Dibatalkan
                        </button>
                    </div>
                </div>
                
                <!-- Orders Table -->
                <div class="orders-table-container">
                    <div class="table-header">
                        <h3><i class="fas fa-table"></i> Daftar Pesanan</h3>
                        <div style="display: flex; align-items: center; gap: 10px;">
                            <span style="font-size: 13px; color: var(--gray);" id="orderCount">0 pesanan</span>
                            <button class="refresh-btn" id="refreshBtn">
                                <i class="fas fa-sync-alt"></i> Refresh
                            </button>
                        </div>
                    </div>
                    
                    <table class="orders-table">
                        <thead>
                            <tr>
                                <th>ID Pesanan</th>
                                <th>Pelanggan</th>
                                <th>Produk</th>
                                <th>Jumlah</th>
                                <th>Total</th>
                                <th>Metode Bayar</th>
                                <th>Status</th>
                                <th>Tanggal</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="ordersTableBody">
                            <!-- Data akan dimuat otomatis -->
                        </tbody>
                    </table>
                    
                    <div id="noOrdersMessage" class="no-orders" style="display: none;">
                        <i class="fas fa-shopping-cart"></i>
                        <h3>Belum ada pesanan</h3>
                        <p>Pesanan dari pelanggan akan muncul di sini</p>
                    </div>
                </div>
            </div>
        </main>
    </div>
    
    <!-- Order Detail Modal -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <button class="close-modal" id="closeDetailModal">&times;</button>
            <div class="modal-header">
                <h2><i class="fas fa-file-invoice"></i> Detail Pesanan</h2>
            </div>
            <div class="modal-body" id="orderDetailContent">
                <!-- Content akan diisi oleh JavaScript -->
            </div>
            <div class="modal-footer">
                <select class="status-select" id="statusSelect">
                    <option value="pending">Menunggu Konfirmasi</option>
                    <option value="processing">Sedang Diproses</option>
                    <option value="completed">Selesai</option>
                    <option value="cancelled">Dibatalkan</option>
                </select>
                <div style="display: flex; gap: 10px; width: 100%;">
                    <button class="btn btn-secondary" id="closeDetailBtn" style="flex: 1;">
                        <i class="fas fa-times"></i> Tutup
                    </button>
                    <button class="btn" id="updateStatusBtn" style="flex: 1;">
                        <i class="fas fa-save"></i> Update
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ==================== KONFIGURASI ====================
        const ADMIN_CREDENTIALS = {
            username: "admin",
            password: "admin123"
        };
        
        const STORAGE_KEYS = {
            ORDERS: 'pangsit_admin_orders',
            NEW_ORDER_FLAG: 'pangsit_new_order',
            LAST_CHECK: 'pangsit_last_order_time',
            SYNC_VERSION: 'pangsit_sync_version'
        };
        
        // ==================== VARIABEL GLOBAL ====================
        let orders = [];
        let lastOrderCount = 0;
        let currentFilter = 'all';
        let currentSearch = '';
        let monitoringInterval = null;
        let syncInterval = null;
        let currentOrderId = null;
        let isAdminPageVisible = false;
        let lastSyncTime = 0;
        let syncVersion = 0;
        
        // ==================== FUNGSI UTAMA ====================
        
        // Format Rupiah
        function formatRupiah(amount) {
            if (!amount) return 'Rp 0';
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }
        
        // Format Tanggal
        function formatDate(dateString) {
            if (!dateString) return '-';
            try {
                const date = new Date(dateString);
                if (isNaN(date.getTime())) {
                    return dateString;
                }
                return date.toLocaleDateString('id-ID', {
                    day: 'numeric',
                    month: 'short',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                });
            } catch (e) {
                return dateString;
            }
        }
        
        // Format waktu lalu
        function timeAgo(timestamp) {
            const now = Date.now();
            const diff = now - timestamp;
            
            const minute = 60 * 1000;
            const hour = 60 * minute;
            const day = 24 * hour;
            
            if (diff < minute) return 'Baru saja';
            if (diff < hour) return `${Math.floor(diff / minute)} menit lalu`;
            if (diff < day) return `${Math.floor(diff / hour)} jam lalu`;
            return `${Math.floor(diff / day)} hari lalu`;
        }
        
        // Deteksi perangkat
        function detectDevice() {
            const ua = navigator.userAgent;
            if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(ua)) {
                return '📱 Mobile';
            } else if (/Tablet|iPad/i.test(ua)) {
                return '📟 Tablet';
            } else {
                return '💻 Desktop';
            }
        }
        
        // Update UI dengan info perangkat
        function updateDeviceInfo() {
            const deviceInfo = document.getElementById('deviceInfo');
            deviceInfo.textContent = ` | ${detectDevice()}`;
        }
        
        // Update waktu terakhir update
        function updateLastUpdateTime() {
            const lastUpdateElement = document.getElementById('lastUpdateTime');
            lastUpdateElement.textContent = `Update: ${timeAgo(lastSyncTime)}`;
        }
        
        // Update status koneksi
        function updateConnectionStatus(isOnline) {
            const statusElement = document.getElementById('connectionStatus');
            const statusText = document.getElementById('statusText');
            
            if (isOnline) {
                statusElement.classList.remove('offline');
                statusText.textContent = 'Online';
            } else {
                statusElement.classList.add('offline');
                statusText.textContent = 'Offline';
            }
        }
        
        // Cek koneksi internet
        function checkConnection() {
            const isOnline = navigator.onLine;
            updateConnectionStatus(isOnline);
            return isOnline;
        }
        
        // Load orders dari localStorage
        function loadOrders() {
            try {
                const stored = localStorage.getItem(STORAGE_KEYS.ORDERS);
                orders = stored ? JSON.parse(stored) : [];
                // Sort by timestamp (newest first)
                orders.sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0));
                
                // Update sync version
                const storedVersion = localStorage.getItem(STORAGE_KEYS.SYNC_VERSION);
                syncVersion = storedVersion ? parseInt(storedVersion) : 0;
                
                return orders;
            } catch (error) {
                console.error('Error loading orders:', error);
                orders = [];
                return [];
            }
        }
        
        // Save orders ke localStorage
        function saveOrders() {
            try {
                localStorage.setItem(STORAGE_KEYS.ORDERS, JSON.stringify(orders));
                syncVersion++;
                localStorage.setItem(STORAGE_KEYS.SYNC_VERSION, syncVersion.toString());
                lastSyncTime = Date.now();
                updateLastUpdateTime();
                return true;
            } catch (error) {
                console.error('Error saving orders:', error);
                return false;
            }
        }
        
        // Update Statistics
        function updateStats() {
            try {
                const pendingCount = orders.filter(o => o.status === 'pending').length;
                const processingCount = orders.filter(o => o.status === 'processing').length;
                const completedCount = orders.filter(o => o.status === 'completed').length;
                const totalOrdersCount = orders.length;
                
                document.getElementById('pendingCount').textContent = pendingCount;
                document.getElementById('processingCount').textContent = processingCount;
                document.getElementById('completedCount').textContent = completedCount;
                document.getElementById('totalOrdersCount').textContent = totalOrdersCount;
                document.getElementById('orderCount').textContent = `${totalOrdersCount} pesanan`;
            } catch (error) {
                console.error('Error updating stats:', error);
            }
        }
        
        // Check if order is new (last 2 minutes)
        function isNewOrder(order) {
            try {
                const twoMinutesAgo = Date.now() - (2 * 60 * 1000);
                return (order.timestamp || 0) > twoMinutesAgo;
            } catch (e) {
                return false;
            }
        }
        
        // Render Orders Table
        function renderOrdersTable(filteredOrders = orders) {
            try {
                const tbody = document.getElementById('ordersTableBody');
                const noOrdersMessage = document.getElementById('noOrdersMessage');
                
                tbody.innerHTML = '';
                
                if (filteredOrders.length === 0) {
                    noOrdersMessage.style.display = 'block';
                    return;
                }
                
                noOrdersMessage.style.display = 'none';
                
                filteredOrders.forEach((order) => {
                    const row = document.createElement('tr');
                    
                    // Check if order is new
                    if (isNewOrder(order)) {
                        row.classList.add('new-order');
                        // Remove new-order class after animation
                        setTimeout(() => {
                            row.classList.remove('new-order');
                        }, 2000);
                    }
                    
                    // Calculate total items
                    const totalItems = order.products ? 
                        order.products.reduce((sum, product) => sum + (product.quantity || 1), 0) : 0;
                    
                    // Status badge
                    let statusClass, statusText;
                    switch(order.status) {
                        case 'pending':
                            statusClass = 'status-pending';
                            statusText = 'Menunggu';
                            break;
                        case 'processing':
                            statusClass = 'status-processing';
                            statusText = 'Diproses';
                            break;
                        case 'completed':
                            statusClass = 'status-completed';
                            statusText = 'Selesai';
                            break;
                        case 'cancelled':
                            statusClass = 'status-cancelled';
                            statusText = 'Dibatalkan';
                            break;
                        default:
                            statusClass = 'status-pending';
                            statusText = 'Menunggu';
                    }
                    
                    row.innerHTML = `
                        <td class="order-id">${order.id || 'N/A'}</td>
                        <td>
                            <div class="customer-info">
                                <div class="customer-name">${order.customer?.name || 'Tidak ada nama'}</div>
                                <div class="customer-phone">${order.customer?.phone || 'Tidak ada telepon'}</div>
                            </div>
                        </td>
                        <td>
                            <ul class="product-list">
                                ${order.products ? order.products.map(p => 
                                    `<li>${p.name || 'Produk'} x${p.quantity || 1}</li>`
                                ).join('') : '<li>Tidak ada produk</li>'}
                            </ul>
                        </td>
                        <td>${totalItems} item</td>
                        <td>${formatRupiah(order.total || 0)}</td>
                        <td>${order.paymentMethod ? order.paymentMethod.toUpperCase() : 'N/A'}</td>
                        <td>
                            <span class="status-badge ${statusClass}">${statusText}</span>
                        </td>
                        <td>${formatDate(order.date || order.timestamp)}</td>
                        <td>
                            <div class="action-buttons">
                                <button class="action-btn view" data-id="${order.id || ''}" title="Lihat Detail">
                                    <i class="fas fa-eye"></i>
                                </button>
                            </div>
                        </td>
                    `;
                    
                    tbody.appendChild(row);
                });
                
                // Add event listeners
                attachOrderActions();
            } catch (error) {
                console.error('Error rendering orders table:', error);
                document.getElementById('noOrdersMessage').style.display = 'block';
            }
        }
        
        // Sinkronisasi data antar perangkat
        function syncData() {
            try {
                if (!checkConnection()) return false;
                
                // Cek perubahan di localStorage
                const currentOrders = loadOrders();
                const currentVersion = syncVersion;
                
                // Cek untuk pesanan baru dari sessionStorage (cross-device communication)
                const sessionOrders = sessionStorage.getItem('pangsit_cross_device_orders');
                if (sessionOrders) {
                    try {
                        const newOrders = JSON.parse(sessionOrders);
                        let hasNewData = false;
                        
                        newOrders.forEach(newOrder => {
                            const existingOrder = currentOrders.find(o => o.id === newOrder.id);
                            if (!existingOrder) {
                                currentOrders.unshift(newOrder);
                                hasNewData = true;
                            }
                        });
                        
                        if (hasNewData) {
                            orders = currentOrders;
                            saveOrders();
                            showNotification('🔄 Data tersinkronisasi dari perangkat lain', 'info');
                        }
                        
                        // Clear sessionStorage setelah diproses
                        sessionStorage.removeItem('pangsit_cross_device_orders');
                    } catch (e) {
                        console.log('Error parsing session orders:', e);
                    }
                }
                
                // Cek flag untuk pesanan baru
                const newOrderFlag = localStorage.getItem(STORAGE_KEYS.NEW_ORDER_FLAG);
                const newOrderTime = localStorage.getItem(STORAGE_KEYS.LAST_CHECK);
                
                let hasNewOrders = false;
                
                // Method 1: Check order count
                if (currentOrders.length > lastOrderCount) {
                    hasNewOrders = true;
                    orders = currentOrders;
                    lastOrderCount = currentOrders.length;
                }
                // Method 2: Check for new order flag
                else if (newOrderFlag) {
                    try {
                        const newOrderData = JSON.parse(newOrderFlag);
                        const existingOrder = orders.find(o => o.id === newOrderData.id);
                        if (!existingOrder) {
                            hasNewOrders = true;
                            orders.unshift(newOrderData);
                            saveOrders();
                        }
                    } catch (e) {
                        console.log('Cannot parse new order flag');
                    }
                }
                // Method 3: Check for recent order timestamp
                else if (newOrderTime) {
                    const lastOrderTime = parseInt(newOrderTime);
                    const fiveMinutesAgo = Date.now() - (5 * 60 * 1000);
                    if (lastOrderTime > fiveMinutesAgo) {
                        orders = loadOrders();
                        hasNewOrders = true;
                    }
                }
                
                // Method 4: Check sync version for changes
                const storedVersion = localStorage.getItem(STORAGE_KEYS.SYNC_VERSION);
                if (storedVersion && parseInt(storedVersion) > currentVersion) {
                    orders = loadOrders();
                    hasNewOrders = true;
                }
                
                // If new orders detected, update display
                if (hasNewOrders) {
                    lastOrderCount = orders.length;
                    
                    // Apply current filter
                    let filteredOrders = orders;
                    if (currentFilter !== 'all') {
                        filteredOrders = orders.filter(o => o.status === currentFilter);
                    }
                    if (currentSearch) {
                        filteredOrders = filteredOrders.filter(o => 
                            (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                            (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch))
                        );
                    }
                    
                    renderOrdersTable(filteredOrders);
                    updateStats();
                    
                    // Show notification
                    if (newOrderFlag) {
                        try {
                            const newOrder = JSON.parse(newOrderFlag);
                            showNotification(
                                `📦 <strong>PESANAN BARU!</strong><br>
                                 ID: ${newOrder.id}<br>
                                 👤 ${newOrder.customer || 'Pelanggan'}<br>
                                 💰 ${formatRupiah(newOrder.total)}`,
                                'success'
                            );
                        } catch (e) {
                            showNotification('📦 Pesanan baru masuk!', 'success');
                        }
                        localStorage.removeItem(STORAGE_KEYS.NEW_ORDER_FLAG);
                    }
                    
                    lastSyncTime = Date.now();
                    updateLastUpdateTime();
                    return true;
                }
                
                lastSyncTime = Date.now();
                updateLastUpdateTime();
                return false;
            } catch (error) {
                console.error('Error syncing data:', error);
                return false;
            }
        }
        
        // Check for new orders (main function)
        function checkForNewOrders() {
            if (!isAdminPageVisible) return;
            syncData();
        }
        
        // Filter orders
        function filterOrders(status) {
            currentFilter = status;
            if (status === 'all') return orders;
            return orders.filter(o => o.status === status);
        }
        
        // Search orders
        function searchOrders(query) {
            currentSearch = query.toLowerCase();
            return orders.filter(o => 
                (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch)) ||
                (o.customer?.phone && o.customer.phone.includes(query))
            );
        }
        
        // Show order detail
        function showOrderDetail(orderId) {
            try {
                const order = orders.find(o => o.id === orderId);
                if (!order) {
                    showNotification('Pesanan tidak ditemukan', 'error');
                    return;
                }
                
                const content = document.getElementById('orderDetailContent');
                
                // Format payment method
                let paymentMethodText = order.paymentMethod || 'N/A';
                switch(paymentMethodText.toLowerCase()) {
                    case 'gopay': paymentMethodText = 'GoPay'; break;
                    case 'ovo': paymentMethodText = 'OVO'; break;
                    case 'dana': paymentMethodText = 'DANA'; break;
                    case 'transfer': paymentMethodText = 'Transfer Bank'; break;
                    case 'qris': paymentMethodText = 'QRIS'; break;
                }
                
                // Format status
                let statusText = 'Menunggu Konfirmasi';
                switch(order.status) {
                    case 'processing': statusText = 'Sedang Diproses'; break;
                    case 'completed': statusText = 'Selesai'; break;
                    case 'cancelled': statusText = 'Dibatalkan'; break;
                }
                
                content.innerHTML = `
                    <div class="order-details-grid">
                        <div>
                            <div class="detail-section">
                                <h3><i class="fas fa-info-circle"></i> Informasi Pesanan</h3>
                                <div class="detail-item">
                                    <span class="detail-label">ID Pesanan:</span>
                                    <span><strong>${order.id || 'N/A'}</strong></span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Tanggal:</span>
                                    <span>${formatDate(order.date || order.timestamp)}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Status:</span>
                                    <span><strong>${statusText}</strong></span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Catatan:</span>
                                    <span>${order.notes || 'Tidak ada catatan'}</span>
                                </div>
                            </div>
                            
                            <div class="detail-section">
                                <h3><i class="fas fa-user"></i> Informasi Pelanggan</h3>
                                <div class="detail-item">
                                    <span class="detail-label">Nama:</span>
                                    <span>${order.customer?.name || 'Tidak ada nama'}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Telepon:</span>
                                    <span>${order.customer?.phone || 'Tidak ada telepon'}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Alamat:</span>
                                    <span>${order.customer?.address || 'Tidak ada alamat'}</span>
                                </div>
                            </div>
                        </div>
                        
                        <div>
                            <div class="detail-section">
                                <h3><i class="fas fa-credit-card"></i> Informasi Pembayaran</h3>
                                <div class="detail-item">
                                    <span class="detail-label">Metode:</span>
                                    <span>${paymentMethodText}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Subtotal:</span>
                                    <span>${formatRupiah(order.subtotal || 0)}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Pengiriman:</span>
                                    <span>${formatRupiah(order.shipping || 0)}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Pajak:</span>
                                    <span>${formatRupiah(order.tax || 0)}</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-label">Total:</span>
                                    <span><strong style="color: var(--primary);">${formatRupiah(order.total || 0)}</strong></span>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="detail-section">
                        <h3><i class="fas fa-box"></i> Detail Produk</h3>
                        <table class="items-table">
                            <thead>
                                <tr>
                                    <th>Produk</th>
                                    <th>Harga</th>
                                    <th>Jumlah</th>
                                    <th>Subtotal</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${order.products ? order.products.map(p => `
                                    <tr>
                                        <td>${p.name || 'Produk'}</td>
                                        <td>${formatRupiah(p.price || 0)}</td>
                                        <td>${p.quantity || 1}</td>
                                        <td>${formatRupiah((p.price || 0) * (p.quantity || 1))}</td>
                                    </tr>
                                `).join('') : `
                                    <tr>
                                        <td colspan="4" style="text-align: center;">Tidak ada produk</td>
                                    </tr>
                                `}
                            </tbody>
                        </table>
                    </div>
                `;
                
                // Set current status in select
                document.getElementById('statusSelect').value = order.status || 'pending';
                
                // Save order ID for update
                document.getElementById('orderDetailModal').dataset.orderId = orderId;
                
                // Show modal
                document.getElementById('orderDetailModal').classList.add('active');
            } catch (error) {
                console.error('Error showing order detail:', error);
                showNotification('Gagal menampilkan detail pesanan', 'error');
            }
        }
        
        // Update order status
        function updateOrderStatus(orderId, newStatus) {
            try {
                const order = orders.find(o => o.id === orderId);
                if (order) {
                    order.status = newStatus;
                    order.updatedAt = new Date().toISOString();
                    
                    // Save to localStorage
                    saveOrders();
                    
                    // Re-render table
                    let filteredOrders = orders;
                    if (currentFilter !== 'all') {
                        filteredOrders = orders.filter(o => o.status === currentFilter);
                    }
                    if (currentSearch) {
                        filteredOrders = filteredOrders.filter(o => 
                            (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                            (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch))
                        );
                    }
                    
                    renderOrdersTable(filteredOrders);
                    updateStats();
                    
                    showNotification(`Status pesanan ${orderId} diubah ke ${newStatus}`, 'success');
                    return true;
                }
                return false;
            } catch (error) {
                console.error('Error updating order status:', error);
                showNotification('Gagal mengupdate status pesanan', 'error');
                return false;
            }
        }
        
        // Attach event listeners to order actions
        function attachOrderActions() {
            // View buttons
            document.querySelectorAll('.action-btn.view').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    if (orderId) {
                        showOrderDetail(orderId);
                    }
                });
            });
        }
        
        // Show notification
        function showNotification(message, type = 'success') {
            try {
                // Remove existing notification
                const existingNotification = document.querySelector('.notification');
                if (existingNotification) {
                    existingNotification.remove();
                }
                
                // Create notification element
                const notification = document.createElement('div');
                notification.className = `notification ${type}`;
                notification.innerHTML = message;
                
                document.body.appendChild(notification);
                
                // Auto remove after 5 seconds
                setTimeout(() => {
                    if (notification.parentNode) {
                        notification.parentNode.removeChild(notification);
                    }
                }, 5000);
            } catch (error) {
                console.error('Error showing notification:', error);
            }
        }
        
        // Start real-time monitoring
        function startMonitoring() {
            // Initial load
            loadOrders();
            lastOrderCount = orders.length;
            lastSyncTime = Date.now();
            
            renderOrdersTable();
            updateStats();
            updateDeviceInfo();
            updateLastUpdateTime();
            checkConnection();
            
            // Start interval for checking new orders (every 1.5 seconds for faster response)
            monitoringInterval = setInterval(checkForNewOrders, 1500);
            
            // Start sync interval for cross-device communication (every 3 seconds)
            syncInterval = setInterval(syncData, 3000);
            
            // Listen for storage events (from other tabs/windows)
            window.addEventListener('storage', function(e) {
                if (e.key === STORAGE_KEYS.ORDERS || 
                    e.key === STORAGE_KEYS.NEW_ORDER_FLAG || 
                    e.key === STORAGE_KEYS.SYNC_VERSION) {
                    checkForNewOrders();
                }
            });
            
            // Listen for online/offline events
            window.addEventListener('online', () => {
                checkConnection();
                checkForNewOrders();
            });
            
            window.addEventListener('offline', () => {
                checkConnection();
            });
            
            // Also check when window gets focus (user comes back to tab)
            window.addEventListener('focus', function() {
                checkForNewOrders();
            });
            
            // Check for new orders when page becomes visible
            document.addEventListener('visibilitychange', function() {
                if (!document.hidden) {
                    checkForNewOrders();
                }
            });
            
            console.log('🔔 Monitoring pesanan diaktifkan - Siap menerima pesanan dari HP & Laptop');
            showNotification('✅ Sistem monitoring aktif! Siap menerima pesanan dari HP & Laptop', 'success');
        }
        
        // Stop monitoring
        function stopMonitoring() {
            if (monitoringInterval) {
                clearInterval(monitoringInterval);
                monitoringInterval = null;
            }
            if (syncInterval) {
                clearInterval(syncInterval);
                syncInterval = null;
            }
        }
        
        // Initialize admin dashboard
        function initAdmin() {
            isAdminPageVisible = true;
            startMonitoring();
            
            // Filter buttons
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    
                    currentFilter = this.getAttribute('data-status');
                    const filtered = filterOrders(currentFilter);
                    renderOrdersTable(filtered);
                });
            });
            
            // Search input
            document.getElementById('searchOrders').addEventListener('input', function() {
                const query = this.value;
                if (query.trim() === '') {
                    const filtered = filterOrders(currentFilter);
                    renderOrdersTable(filtered);
                } else {
                    const filtered = searchOrders(query);
                    renderOrdersTable(filtered);
                }
            });
            
            // Refresh button
            document.getElementById('refreshBtn').addEventListener('click', function() {
                const icon = this.querySelector('i');
                icon.classList.add('rotating');
                loadOrders();
                syncData();
                setTimeout(() => {
                    icon.classList.remove('rotating');
                }, 1000);
            });
            
            // Modal close buttons
            document.getElementById('closeDetailModal').addEventListener('click', () => {
                document.getElementById('orderDetailModal').classList.remove('active');
            });
            
            document.getElementById('closeDetailBtn').addEventListener('click', () => {
                document.getElementById('orderDetailModal').classList.remove('active');
            });
            
            document.getElementById('orderDetailModal').addEventListener('click', (e) => {
                if (e.target === document.getElementById('orderDetailModal')) {
                    document.getElementById('orderDetailModal').classList.remove('active');
                }
            });
            
            // Update status button
            document.getElementById('updateStatusBtn').addEventListener('click', () => {
                const orderId = document.getElementById('orderDetailModal').dataset.orderId;
                const newStatus = document.getElementById('statusSelect').value;
                
                if (orderId && updateOrderStatus(orderId, newStatus)) {
                    document.getElementById('orderDetailModal').classList.remove('active');
                }
            });
            
            // Logout button
            document.getElementById('logoutBtn').addEventListener('click', () => {
                isAdminPageVisible = false;
                stopMonitoring();
                localStorage.removeItem('pangsit_admin_logged_in');
                document.getElementById('adminPage').style.display = 'none';
                document.getElementById('loginPage').style.display = 'flex';
            });
            
            // Add event listener to stat cards for filtering
            document.querySelectorAll('.stat-card[data-filter]').forEach(card => {
                card.addEventListener('click', function() {
                    const filter = this.getAttribute('data-filter');
                    const filterBtn = document.querySelector(`.filter-btn[data-status="${filter}"]`);
                    if (filterBtn) {
                        filterBtn.click();
                    }
                });
            });
        }
        
        // Login function
        function initLogin() {
            document.getElementById('loginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                const errorElement = document.getElementById('loginError');
                
                if (username === ADMIN_CREDENTIALS.username && password === ADMIN_CREDENTIALS.password) {
                    errorElement.style.display = 'none';
                    localStorage.setItem('pangsit_admin_logged_in', 'true');
                    
                    document.getElementById('loginPage').style.display = 'none';
                    document.getElementById('adminPage').style.display = 'block';
                    
                    initAdmin();
                } else {
                    errorElement.style.display = 'block';
                }
            });
        }
        
        // Initialize on page load
        document.addEventListener('DOMContentLoaded', () => {
            // Auto-fill login for testing
            document.getElementById('username').value = 'admin';
            document.getElementById('password').value = 'admin123';
            
            // Check if already logged in
            const isLoggedIn = localStorage.getItem('pangsit_admin_logged_in') === 'true';
            
            if (isLoggedIn) {
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('adminPage').style.display = 'block';
                initAdmin();
            } else {
                document.getElementById('loginPage').style.display = 'flex';
                document.getElementById('adminPage').style.display = 'none';
                initLogin();
            }
            
            // Add touch event support for mobile
            document.addEventListener('touchstart', function(){}, {passive: true});
            
            // Handle orientation change
            window.addEventListener('orientationchange', function() {
                setTimeout(checkForNewOrders, 300);
            });
        });
    </script>
</body>
</html>
